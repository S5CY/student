---
layout: base
title: Snake Game
permalink: /snake/
---

<style>
  body { font-family: sans-serif; background: #111; color: #fff; text-align: center; }
  h2 { margin-top: 20px; }
  #game-container { margin: auto; display: inline-block; position: relative; }
  canvas {
    display: block;
    background: #222;
    margin: auto;
    border-radius: 8px;
  }
  #score {
    font-size: 24px;
    margin: 10px 0;
  }
  #gameover {
    display: none;
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 28px;
    color: white;
    background: rgba(0,0,0,0.8);
    padding: 20px;
    border-radius: 10px;
  }
  #gameover button {
    margin-top: 10px;
    padding: 8px 16px;
    border: none;
    background: #4CAF50;
    color: #fff;
    font-size: 18px;
    border-radius: 5px;
    cursor: pointer;
  }
  #gameover button:hover {
    background: #45a049;
  }
</style>

<h2>Snake Game</h2>
<div id="game-container">
  <div id="score">Score: <span id="score_value">0</span></div>
  <canvas id="snake" width="400" height="400"></canvas>
  <div id="gameover">
    <p>Game Over!</p>
    <button id="restart">Play Again</button>
  </div>
</div>

<script>
(function(){
  const canvas = document.getElementById("snake");
  const ctx = canvas.getContext("2d");
  const scoreElem = document.getElementById("score_value");
  const gameOverElem = document.getElementById("gameover");
  const restartBtn = document.getElementById("restart");

  const blockSize = 20;
  const gridSize = canvas.width / blockSize;

  let snake, food, dir, nextDir, score, running;

  function init() {
    snake = [{x: 8, y: 8}];
    dir = nextDir = "RIGHT";
    score = 0;
    updateScore();
    placeFood();
    running = true;
    gameOverElem.style.display = "none";
    loop();
  }

  function updateScore() {
    scoreElem.textContent = score;
  }

  function placeFood() {
    do {
      food = {
        x: Math.floor(Math.random() * gridSize),
        y: Math.floor(Math.random() * gridSize)
      };
    } while (snake.some(p => p.x === food.x && p.y === food.y));
  }

  function drawSnake() {
    snake.forEach((part, i) => {
      if (i === 0) {
        // Head is brighter
        ctx.fillStyle = "#00FF7F";
      } else {
        ctx.fillStyle = "#32CD32";
      }
      ctx.fillRect(part.x * blockSize, part.y * blockSize, blockSize-2, blockSize-2);
    });
  }

  function drawFood() {
    ctx.beginPath();
    ctx.fillStyle = "red";
    ctx.arc(
      food.x * blockSize + blockSize/2,
      food.y * blockSize + blockSize/2,
      blockSize/2 - 2, 0, Math.PI*2
    );
    ctx.fill();
  }

  function moveSnake() {
    const head = {...snake[0]};
    dir = nextDir;

    if (dir === "UP") head.y--;
    if (dir === "DOWN") head.y++;
    if (dir === "LEFT") head.x--;
    if (dir === "RIGHT") head.x++;

    // Wrap around like Google Snake
    head.x = (head.x + gridSize) % gridSize;
    head.y = (head.y + gridSize) % gridSize;

    // Collision with self
    if (snake.some(p => p.x === head.x && p.y === head.y)) {
      gameOver();
      return;
    }

    snake.unshift(head);

    if (head.x === food.x && head.y === food.y) {
      score++;
      updateScore();
      placeFood();
    } else {
      snake.pop();
    }
  }

  function render() {
    ctx.fillStyle = "#222";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    drawSnake();
    drawFood();
  }

  function loop() {
    if (!running) return;
    moveSnake();
    render();
    setTimeout(loop, 100); // speed
  }

  function gameOver() {
    running = false;
    gameOverElem.style.display = "block";
  }

  window.addEventListener("keydown", e => {
    if (e.key === "ArrowUp" && dir !== "DOWN") nextDir = "UP";
    if (e.key === "ArrowDown" && dir !== "UP") nextDir = "DOWN";
    if (e.key === "ArrowLeft" && dir !== "RIGHT") nextDir = "LEFT";
    if (e.key === "ArrowRight" && dir !== "LEFT") nextDir = "RIGHT";
  });

  restartBtn.onclick = init;

  init();
})();
</script>
