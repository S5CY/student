---
layout: base
title: I'm Meryl
hide: true
---

<style>
  /* Pastel color animation with dark text */
  body {
    color: #333;
    transition: background-color 1s ease;
    animation: colorChange 15s infinite;
    line-height: 1.6;
  }
  
  @keyframes colorChange {
    0% { background-color: #FFD1DC; }
    20% { background-color: #B5EAD7; }
    40% { background-color: #C7CEEA; }
    60% { background-color: #E2F0CB; }
    80% { background-color: #FFDAC1; }
    100% { background-color: #FFD1DC; }
  }

  /* Star styles */
  .star {
    position: fixed;
    width: 3px;
    height: 3px;
    background: rgba(80,80,80,0.8);
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

  /* Text styles */
  h1, h2, h3, h4, h5, h6 {
    color: #222 !important;
    font-weight: 600;
  }
  
  /* Table styles - updated with beautiful colors */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.5rem 0;
    background: rgba(255,255,255,0.97);
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border-radius: 12px;
    overflow: hidden;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  }
  
  th {
    background: linear-gradient(135deg, #8A6BBE, #6b4bd3);
    color: white !important;
    padding: 14px;
    text-align: left;
    font-weight: 500;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    font-size: 0.85em;
  }
  
  td {
    padding: 12px 14px;
    border-bottom: 1px solid #f0f0f0;
    color: #333 !important;
    transition: all 0.2s ease;
  }
  
  tr:last-child td {
    border-bottom: none;
  }
  
  tr:hover td {
    background-color: rgba(138, 107, 190, 0.08);
    color: #222 !important;
  }
  
  /* Button styles */
  .button.small {
    background: linear-gradient(135deg, #8A6BBE, #6b4bd3) !important;
    border: none;
    color: white !important;
    font-weight: 500;
    padding: 10px 20px;
    border-radius: 25px;
    box-shadow: 0 4px 8px rgba(107, 75, 211, 0.2);
    transition: all 0.3s ease;
    display: inline-block;
    margin: 0.2rem;
    text-decoration: none;
  }
  
  .button.small:hover {
    background: linear-gradient(135deg, #7A5BAE, #5a3dba) !important;
    transform: translateY(-3px);
    box-shadow: 0 6px 12px rgba(107, 75, 211, 0.3);
    text-decoration: none;
  }
  
  /* Link styles */
  a {
    color: #6b4bd3 !important;
    font-weight: 500;
    transition: all 0.2s ease;
    text-decoration: none;
  }
  
  a:hover {
    color: #4a2d9e !important;
    text-decoration: underline;
  }
  
  /* Contact section */
  #contact {
    background: rgba(255,255,255,0.97);
    padding: 1.8rem;
    border-radius: 12px;
    margin-top: 2.5rem;
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    border: 1px solid rgba(0,0,0,0.05);
  }
  
  #contact p {
    color: #333 !important;
    margin-bottom: 0.8rem;
  }
  
  /* Badge styles */
  .badge {
    transition: all 0.3s ease;
    border-radius: 6px;
    padding: 2px 6px;
    display: inline-block;
    margin: 0.2rem;
  }
  
  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
</style>

<script>
  // Create stars
  function createStars() {
    const starsCount = 30;
    for (let i = 0; i < starsCount; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      
      // Random position
      star.style.left = Math.random() * 100 + 'vw';
      star.style.top = Math.random() * 100 + 'vh';
      
      // Random size
      const size = Math.random() * 3 + 1;
      star.style.width = size + 'px';
      star.style.height = size + 'px';
      
      // Random animation
      star.style.animationDuration = (Math.random() * 10 + 5) + 's';
      star.style.animationDelay = Math.random() * 5 + 's';
      
      document.body.appendChild(star);
    }
  }

  // Initialize stars
  window.addEventListener('load', createStars);

  // Background colors cycling
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
  
  setInterval(changeBackground, 3000);
</script>

### Me and Team

Hi! My name is Meryl.

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