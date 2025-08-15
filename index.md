---
layout: base
title: I'm [Your Full Name]
hide: true
---

<style>
  body {
    color: white;
    transition: all 0.5s ease;
    animation: colorChange 10s infinite;
    font-family: 'Comic Sans MS', cursive, sans-serif;
    overflow-x: hidden;
  }
  
  @keyframes colorChange {
    0% { background-color: #FF5733; }
    10% { background-color: #33FF57; }
    20% { background-color: #3357FF; }
    30% { background-color: #F333FF; }
    40% { background-color: #FF33F3; }
    50% { background-color: #33FFF5; }
    60% { background-color: #F5FF33; }
    70% { background-color: #FF8C33; }
    80% { background-color: #8C33FF; }
    90% { background-color: #33FF8C; }
    100% { background-color: #FF5733; }
  }

  .floating {
    position: fixed;
    animation: float 10s infinite ease-in-out;
    z-index: -1;
    opacity: 0.7;
    filter: blur(1px);
  }

  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    25% { transform: translate(50vw, 25vh) rotate(90deg); }
    50% { transform: translate(25vw, 50vh) rotate(180deg); }
    75% { transform: translate(75vw, 25vh) rotate(270deg); }
    100% { transform: translate(0, 0) rotate(360deg); }
  }

  .emoji-rain {
    position: fixed;
    top: -50px;
    animation: rain linear infinite;
    z-index: -1;
  }

  @keyframes rain {
    to { transform: translateY(100vh); }
  }

  .matrix-code {
    position: fixed;
    bottom: 0;
    color: lime;
    font-family: monospace;
    z-index: -1;
    writing-mode: vertical-rl;
    text-orientation: upright;
    animation: matrix 5s linear infinite;
  }

  @keyframes matrix {
    from { transform: translateY(-100%); }
    to { transform: translateY(100%); }
  }

  .pulsing-text {
    animation: pulse 1s infinite alternate;
    text-shadow: 0 0 10px currentColor;
  }

  @keyframes pulse {
    from { transform: scale(1); }
    to { transform: scale(1.05); }
  }
</style>

<!-- Abstract floating shapes -->
<div class="floating" style="top:20%; left:10%; font-size:50px;">🦄</div>
<div class="floating" style="top:70%; left:80%; font-size:70px;">🍕</div>
<div class="floating" style="top:40%; left:60%; font-size:40px;">👽</div>
<div class="floating" style="top:10%; left:50%; font-size:60px;">🤖</div>

<!-- Emoji rain -->
<script>
  function createEmojiRain() {
    const emojis = ['💻', '🚀', '🌈', '🎮', '🍔', '🐱', '👾', '🦕'];
    const emoji = document.createElement('div');
    emoji.className = 'emoji-rain';
    emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
    emoji.style.left = Math.random() * 100 + 'vw';
    emoji.style.fontSize = (Math.random() * 20 + 10) + 'px';
    emoji.style.animationDuration = (Math.random() * 3 + 2) + 's';
    document.body.appendChild(emoji);
    
    setTimeout(() => {
      emoji.remove();
    }, 5000);
  }
  
  setInterval(createEmojiRain, 300);
</script>

<!-- Matrix code effect -->
<div class="matrix-code" style="left: 5%;">01010101010101010101010101010101</div>
<div class="matrix-code" style="left: 10%;">10101010101010101010101010101010</div>
<div class="matrix-code" style="right: 5%;">01010101010101010101010101010101</div>
<div class="matrix-code" style="right: 10%;">10101010101010101010101010101010</div>

<!-- Main content with pulsing effect -->
<div class="pulsing-text">
### Me and Team

Hi! My name is [Your Full Name].

| Role         | Name     | Repo Location                       | Stream                | Repo Name |
|--------------|----------|-------------------------------------|-----------------------|-----------|
| Scrum Master | John     | github.com/jm1021/student           | upstream (OCS fork)   | student   |
| Scrummer     | Torin    | github.com/torin/student            | downstream (fork)     | student   |
| Scrummer     | Avantika | github.com/avantika/student         | downstream (fork)     | student   |
| Scrummer     | Aadit    | github.com/aaadit/student           | downstream (fork)     | student   |


## Links to Learning

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<a href="https://github.com/Open-Coding-Society/student">
    <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub">
</a>
<a href="https://open-coding-society.github.io/student">
    <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?logo=github&logoColor=white" alt="GitHub Pages">
</a>
<a href="https://kasm.opencodingsociety.com/" class="button small" style="background-color: #6b4bd3ff">
    KASM
</a>
<a href="https://vscode.dev/" class="button small" style="background-color: #4baad3ff">
    <span style="color: #3e77ceff">VSCODE</span>
</a>

<br>

### Class Progress

<a href="{{site.baseurl}}/snake" class="button small" style="background-color: #6b4bd3ff">
    Snake Game
</a>
<a href="{{site.baseurl}}/turtle" class="button small" style="background-color: #2A7DB1">
    <span style="color: #000000">Turtle</span>
</a>

<br>

<!-- Contact Section -->
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p style="color: #2A7DB1;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #2A7DB1; text-decoration: underline;">Socials</a></p>
</div>

<script>
  // Dynamic background color changing
  const colors = [
    '#FF5733', '#33FF57', '#3357FF', '#F333FF', 
    '#FF33F3', '#33FFF5', '#F5FF33', '#FF8C33',
    '#8C33FF', '#33FF8C', '#FF3361', '#61FF33',
    '#3361FF', '#FF33A8', '#A833FF'
  ];
  
  let currentIndex = 0;
  
  function changeBackground() {
    document.body.style.backgroundColor = colors[currentIndex];
    currentIndex = (currentIndex + 1) % colors.length;
  }
  
  setInterval(changeBackground, 500);

  // Random mouse trail effect
  document.addEventListener('mousemove', function(e) {
    const trail = document.createElement('div');
    trail.className = 'floating';
    trail.style.left = e.pageX + 'px';
    trail.style.top = e.pageY + 'px';
    trail.style.fontSize = '20px';
    trail.textContent = ['✨', '🌟', '⚡', '💫'][Math.floor(Math.random() * 4)];
    document.body.appendChild(trail);
    
    setTimeout(() => {
      trail.remove();
    }, 1000);
  });
</script>