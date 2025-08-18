---
layout: base
title: I'm [Your Full Name]
hide: true
---

<style>
  /* Pastel background colors */
  body {
    color: #333;
    transition: background-color 1s ease;
    animation: colorChange 15s infinite;
  }
  
  @keyframes colorChange {
    0% { background-color: #FFD1DC; } /* Pastel pink */
    20% { background-color: #B5EAD7; } /* Pastel mint */
    40% { background-color: #C7CEEA; } /* Pastel lavender */
    60% { background-color: #E2F0CB; } /* Pastel green */
    80% { background-color: #FFDAC1; } /* Pastel peach */
    100% { background-color: #FFD1DC; } /* Pastel pink */
  }

  /* 星星样式 */
  .star {
    position: fixed;
    width: 3px;
    height: 3px;
    background: rgba(0,0,0,0.3);
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

  /* 现代表格样式 */
  .team-table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 0;
    margin: 2rem 0;
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  }
  
  .team-table th {
    background: #6b4bd3;
    color: white;
    padding: 15px;
    text-align: left;
    font-weight: 500;
  }
  
  .team-table td {
    padding: 12px 15px;
    border-bottom: 1px solid #f0f0f0;
  }
  
  .team-table tr:last-child td {
    border-bottom: none;
  }
  
  .team-table tr:hover {
    background-color: #f8f7ff;
  }
  
  .team-table tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  
  .team-table tr:nth-child(even):hover {
    background-color: #f0efff;
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

  // 更柔和的背景颜色变换
  const pastelColors = [
    '#FFD1DC', '#B5EAD7', '#C7CEEA', 
    '#E2F0CB', '#FFDAC1', '#B5EAD7',
    '#A2D2FF', '#CDB4DB', '#FFC8DD'
  ];
  
  let currentIndex = 0;
  
  function changeBackground() {
    document.body.style.backgroundColor = pastelColors[currentIndex];
    currentIndex = (currentIndex + 1) % pastelColors.length;
  }
  
  // 更慢的颜色变换 (3秒)
  setInterval(changeBackground, 3000);
</script>

### Me and Team

Hi! My name is [Your Full Name].

<table class="team-table">
  <thead>
    <tr>
      <th>Role</th>
      <th>Name</th>
      <th>Repo Location</th>
      <th>Stream</th>
      <th>Repo Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Scrum Master</td>
      <td>John</td>
      <td>github.com/jm1021/student</td>
      <td>upstream (OCS fork)</td>
      <td>student</td>
    </tr>
    <tr>
      <td>Scrummer</td>
      <td>Torin</td>
      <td>github.com/torin/student</td>
      <td>downstream (fork)</td>
      <td>student</td>
    </tr>
    <tr>
      <td>Scrummer</td>
      <td>Avantika</td>
      <td>github.com/avantika/student</td>
      <td>downstream (fork)</td>
      <td>student</td>
    </tr>
    <tr>
      <td>Scrummer</td>
      <td>Aadit</td>
      <td>github.com/aaadit/student</td>
      <td>downstream (fork)</td>
      <td>student</td>
    </tr>
  </tbody>
</table>

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

<p style="color: #6b4bd3;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #6b4bd3; text-decoration: underline;">Socials</a></p>