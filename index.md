---
layout: base
title: I'm [Your Full Name]
hide: true
---

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

<style>
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
</style>

<script>
  // More dynamic color changing with JavaScript
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