---
layout: default
title: Background with Object
description: Use JavaScript to have an in motion background.
sprite: /student/images/platformer/sprites/cat.png
background: /student/images/platformer/backgrounds/星空背景.png
permalink: /background
---

<canvas id="world"></canvas>

<script>
  // Get reference to canvas and its 2D drawing context
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');

  // Create Image objects for background and player sprite
  const backgroundImg = new Image();
  const spriteImg = new Image();

  // Assign sources (injected from page front-matter above)
  backgroundImg.src = "{{ page.background }}";
  spriteImg.src = "{{ page.sprite }}";

  // Counter to track when both images have loaded
  let imagesLoaded = 0;

  // Increment counter when background loads
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld(); // Try to start once loaded
  };

  // Increment counter when sprite loads
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld(); // Try to start once loaded
  };

  // Main function to initialize and run the game world
  function startGameWorld() {
    // Only start if both images are fully loaded
    if (imagesLoaded < 2) return;

    // Base class for all objects in the game
    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image;
        this.width = width;
        this.height = height;
        this.x = x;
        this.y = y;
        this.speedRatio = speedRatio;
        this.speed = GameWorld.gameSpeed * this.speedRatio;
      }
      update() {} // Empty update, overridden by subclasses
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }

    // Background object that goes on infinitely
    class Background extends GameObject {
      constructor(image, gameWorld) {
        // Fill the canvas with background image
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        // Move background left, wrap around when off screen
        this.x = (this.x - this.speed) % this.width;
      }
      draw(ctx) {
        // Draw two images side by side to create infinite loop
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }

    // Player object that bobs up and down
    class Player extends GameObject {
      constructor(image, gameWorld) {
        // Scale sprite down by half
        const width = image.naturalWidth / 2;
        const height = image.naturalHeight / 2;

        // Center the player on screen
        const x = (gameWorld.width - width) / 2;
        const y = (gameWorld.height - height) / 2;

        super(image, width, height, x, y);

        // Base Y position and animation frame tracker
        this.baseY = y;
        this.frame = 0;
      }
      update() {
        // Animate player with a sine wave bobbing motion
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }

    // Main game world
    class GameWorld {
      static gameSpeed = 5; // Global scroll speed
      constructor(backgroundImg, spriteImg) {
        // Setup canvas dimensions to match window
        this.canvas = document.getElementById("world");
        this.ctx = this.canvas.getContext('2d');
        this.width = window.innerWidth;
        this.height = window.innerHeight;
        this.canvas.width = this.width;
        this.canvas.height = this.height;

        // Style canvas to fill window
        this.canvas.style.width = `${this.width}px`;
        this.canvas.style.height = `${this.height}px`;
        this.canvas.style.position = 'absolute';
        this.canvas.style.left = `0px`;
        this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

        // Initialize objects: scrolling background + player
        this.gameObjects = [
         new Background(backgroundImg, this),
         new Player(spriteImg, this)
        ];
      }
      // Game loop: update + draw all objects each frame
      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.gameObjects) {
          obj.update();
          obj.draw(this.ctx);
        }
        // Request next animation frame
        requestAnimationFrame(this.gameLoop.bind(this));
      }
      // Start the game loop
      start() {
        this.gameLoop();
      }
    }

    // Create game world and start running
    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
</script>