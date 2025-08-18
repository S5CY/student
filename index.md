---
layout: base
title: I'm Meryl
hide: true
---

<style>
  /* Pastel color animation */
  body {
    color: #555;
    transition: background-color 1s ease;
    animation: colorChange 15s infinite;
  }
  
  @keyframes colorChange {
    0% { background-color: #FFD1DC; } /* Pastel pink */
    20% { background-color: #B5EAD7; } /* Pastel mint */
    40% { background-color: #C7CEEA; } /* Pastel lavender */
    60% { background-color: #E2F0CB; } /* Pastel green */
    80% { background-color: #FFDAC1; } /* Pastel peach */
    100% { background-color: #FFD1DC; }
  }

  /* 星星样式 - updated for pastel background */
  .star {
    position: fixed;
    width: 3px;
    height: 3px;
    background: rgba(100,100,100,0.6);
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

  /* Updated table styling with pastel colors */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.5rem 0;
    background: rgba(255,255,255,0.8);
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border-radius: 10px;
    overflow: hidden;
  }
  
  th {
    background-color: #A2D2FF; /* Pastel blue */
    color: white;
    padding: 12px;
    text-align: left;
  }
  
  td {
    padding: 10px 12px;
    border-bottom: 1px solid #f0f0f0;
  }
  
  tr:hover {
    background-color: rgba(178, 232, 215, 0.3); /* Light pastel mint */
  }
  
  /* Updated button colors */
  .button.small {
    background-color: #CDB4DB !important; /* Pastel purple */
    border: none;
    color: white !important;
  }
  
  /* Updated link colors */
  a {
    color: #6b4bd3;
  }
  
  /* Updated contact section */
  #contact {
    background: rgba(255,255,255,0.7);
    padding: 1.5rem;
    border-radius: 10px;
    margin-top: 2rem;
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

  // Pastel background colors cycling
  const pastelColors = [
    '#FFD1DC', '#B5EAD7', '#C7CEEA', 
    '#E2F0CB', '#FFDAC1', '#A2D2FF',
    '#CDB4DB', '#FFC8DD', '#BDE0FE'
  ];
  
  let currentIndex = 0;
  
  function changeBackground() {
    document.body.style.backgroundColor = pastelColors[currentIndex];
    currentIndex = (currentIndex + 1) % pastelColors.length;
  }
  
  // Change color every 3 seconds (slower transition)
  setInterval(changeBackground, 3000);
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
<a href="https://kasm.opencodingsociety.com/" class="button small">
    KASM
</a>
<a href="https://vscode.dev/" class="button small">
    VSCODE
</a>

<br>

### Class Progress

<a href="{{site.baseurl}}/snake" class="button small">
    Snake Game
</a>
<a href="{{site.baseurl}}/turtle" class="button small">
    Turtle
</a>

<br>

<!-- Contact Section -->
<div id="contact">
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p>Open Coding Society: <a href="https://opencodingsociety.com">Socials</a></p>
</div>