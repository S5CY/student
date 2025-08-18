---
layout: base
title: I'm [Your Full Name]
hide: true
---

<style>
  /* 原有样式 */
  body {
    color: white;
    transition: background-color 0.5s ease;
    animation: colorChange 10s infinite;
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

  /* 星星样式 */
  .star {
    position: fixed;
    width: 3px;
    height: 3px;
    background: white;
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    opacity: 0.8;
    animation: twinkle 1s infinite alternate, float 15s infinite linear;
  }
  
  @keyframes twinkle {
    0% { opacity: 0.3; transform: scale(0.8); }
    100% { opacity: 1; transform: scale(1.2); }
  }
  
  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    100% { transform: translate(100vw, 100vh) rotate(360deg); }
  }
</style>

<script>
  // 创建星星
  function createStars() {
    const starsCount = 30;
    for (let i = 0; i < starsCount; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      
      // 随机位置
      star.style.left = Math.random() * 100 + 'vw';
      star.style.top = Math.random() * 100 + 'vh';
      
      // 随机大小
      const size = Math.random() * 3 + 1;
      star.style.width = size + 'px';
      star.style.height = size + 'px';
      
      // 随机动画持续时间
      star.style.animationDuration = (Math.random() * 10 + 5) + 's';
      
      // 随机延迟
      star.style.animationDelay = Math.random() * 5 + 's';
      
      document.body.appendChild(star);
    }
  }

  // 页面加载后创建星星
  window.addEventListener('load', createStars);

  // 原有JavaScript
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
  
  // Change color every 500ms (0.5 seconds)
  setInterval(changeBackground, 500);
</script>

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