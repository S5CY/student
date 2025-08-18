---
layout: base
title: I'm Meryl
hide: true
---

<style>
  /* Pastel color animation with better contrast */
  body {
    color: #444; /* 深灰色文字，在浅色背景上更清晰 */
    transition: background-color 1s ease;
    animation: colorChange 15s infinite;
    line-height: 1.6;
  }
  
  @keyframes colorChange {
    0% { background-color: #FFD1DC; } /* Pastel pink */
    20% { background-color: #B5EAD7; } /* Pastel mint */
    40% { background-color: #C7CEEA; } /* Pastel lavender */
    60% { background-color: #E2F0CB; } /* Pastel green */
    80% { background-color: #FFDAC1; } /* Pastel peach */
    100% { background-color: #FFD1DC; }
  }

  /* 星星样式 - 调整为更显眼的深色 */
  .star {
    position: fixed;
    width: 3px;
    height: 3px;
    background: rgba(80,80,80,0.8); /* 深灰色星星 */
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    animation: twinkle 1s infinite alternate, float 15s infinite linear;
  }
  
  @keyframes twinkle {
    0% { opacity: 0.5; transform: scale(0.8); }
    100% { opacity: 1; transform: scale(1.2); }
  }
  
  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    100% { transform: translate(100vw, 100vh) rotate(360deg); }
  }

  /* 标题样式 - 增加对比度 */
  h1, h2, h3, h4, h5, h6 {
    color: #333; /* 更深的文字颜色 */
    font-weight: 600;
  }
  
  /* 表格样式 - 提高可读性 */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.5rem 0;
    background: rgba(255,255,255,0.9); /* 更白的背景 */
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border-radius: 10px;
    overflow: hidden;
  }
  
  th {
    background-color: #8A6BBE; /* 更深的紫色 */
    color: white !important; /* 确保白色文字 */
    padding: 12px;
    text-align: left;
    font-weight: 500;
  }
  
  td {
    padding: 10px 12px;
    border-bottom: 1px solid #eee;
    color: #444; /* 深灰色文字 */
  }
  
  tr:hover {
    background-color: rgba(138, 107, 190, 0.1); /* 浅紫色悬停效果 */
  }
  
  /* 按钮样式 - 提高对比度 */
  .button.small {
    background-color: #8A6BBE !important; /* 更深的紫色 */
    border: none;
    color: white !important;
    font-weight: 500;
    text-shadow: 0 1px 1px rgba(0,0,0,0.2);
  }
  
  .button.small:hover {
    background-color: #6b4bd3 !important;
    transform: translateY(-2px);
  }
  
  /* 链接样式 */
  a {
    color: #6b4bd3; /* 深紫色链接 */
    font-weight: 500;
    text-decoration: none;
    transition: color 0.2s;
  }
  
  a:hover {
    color: #4a2d9e;
    text-decoration: underline;
  }
  
  /* 联系区域 - 提高可读性 */
  #contact {
    background: rgba(255,255,255,0.85);
    padding: 1.5rem;
    border-radius: 10px;
    margin-top: 2rem;
    box-shadow: 0 4px 10px rgba(0,0,0,0.08);
  }
  
  #contact p {
    color: #444;
    margin-bottom: 0.5rem;
  }
  
  /* 徽章样式微调 */
  .badge {
    filter: brightness(0.95); /* 稍微加深徽章颜色 */
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
  
  // Change color every 3 seconds
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
    <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub" class="badge">
</a>
<a href="https://open-coding-society.github.io/student">
    <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?logo=github&logoColor=white" alt="GitHub Pages" class="badge">
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