---
layout: base
title: I'm Meryl
hide: true
---

<style>
  :root{
    --ink:#45455a;
    --ink-2:#5a5a77;
    --primary:#6A5ACD;          /* Slate Blue */
    --accent-1:#B5C7EA;         /* 柔蓝 */
    --accent-2:#C7B5EA;         /* 柔紫 */
    --glass-bg: rgba(255,255,255,0.9);
    --glass-brd: rgba(220,220,255,0.55);
    --shadow: 0 8px 24px rgba(120,120,180,0.18);
  }

  html, body {
    margin: 0;
    padding: 0;
  }

  body {
    color: var(--ink);
    line-height: 1.65;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    animation: bgCycle 28s ease-in-out infinite alternate;
    background-attachment: fixed;
  }

  @keyframes bgCycle {
    0%   { background: radial-gradient(1200px 800px at 10% 10%, #FFF0F5 0%, #F0F8FF 55%, #F5F0FF 100%); }
    50%  { background: radial-gradient(1200px 800px at 90% 20%, #F0FFF0 0%, #FFF8F0 60%, #F0F5FF 100%); }
    100% { background: radial-gradient(1200px 800px at 50% 80%, #E6F9FF 0%, #F8F0FF 60%, #FFF0F5 100%); }
  }

  .star {
    position: fixed;
    width: 2px;
    height: 2px;
    background: rgba(180, 180, 255, 0.75);
    border-radius: 50%;
    pointer-events: none;
    z-index: 1;
    animation: twinkle 2.2s infinite alternate ease-in-out, float 38s linear infinite;
  }
  @keyframes twinkle {
    0%   { opacity: .35; transform: scale(.6); }
    100% { opacity: 1;   transform: scale(1); }
  }
  @keyframes float {
    0%   { transform: translate(0, 0) rotate(0deg); }
    100% { transform: translate(70vw, 70vh) rotate(360deg); }
  }

  @media (prefers-reduced-motion: reduce) {
    body { animation: none; }
    .star { animation: none; }
  }

  main {
    position: relative;
    z-index: 2;
    max-width: 980px;
    margin: 40px auto;
    padding: 24px;
    background: var(--glass-bg);
    border: 1px solid var(--glass-brd);
    border-radius: 16px;
    box-shadow: var(--shadow);
    backdrop-filter: blur(6px);
  }

  h1, h2, h3, h4, h5, h6 {
    color: var(--primary) !important;
    font-weight: 560;
    letter-spacing: .2px;
    margin-top: 1.2em;
  }
  h1 { margin-top: 0; }

  p, li { color: var(--ink-2); }

  /* 表格 */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.2rem 0;
    background: #fff;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 10px rgba(150,150,200,0.12);
  }
  th {
    background: linear-gradient(135deg, var(--accent-1), var(--accent-2));
    color: #fff !important;
    padding: 14px;
    text-align: left;
    font-weight: 600;
    letter-spacing: .4px;
    text-transform: uppercase;
    font-size: .83rem;
  }
  td {
    padding: 12px 14px;
    border-bottom: 1px solid #F0F0FF;
    color: #4e4e7a !important; /* 柔和蓝紫色 */
    transition: background-color .2s ease, color .2s ease;
  }
  tr:last-child td { border-bottom: none; }
  tr:hover td {
    background-color: rgba(200,200,255,0.06);
    color: var(--primary) !important;
  }

  .button.small, .badge {
    display: inline-block;
    text-decoration: none;
    margin: .25rem .3rem .25rem 0;
  }
  .button.small {
    background: linear-gradient(135deg, var(--accent-1), var(--accent-2));
    border: none;
    color: #fff !important;
    font-weight: 600;
    padding: 10px 18px;
    border-radius: 22px;
    box-shadow: 0 4px 12px rgba(150, 130, 200, 0.28);
    transition: transform .2s ease, box-shadow .2s ease, filter .2s ease;
  }
  .button.small:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 18px rgba(150, 130, 200, 0.35);
    filter: saturate(1.05);
  }
  .badge {
    padding: 6px 10px;
    border-radius: 10px;
    background-color: rgba(200,200,255,0.22);
    color: var(--primary);
    font-weight: 600;
    transition: transform .2s ease, box-shadow .2s ease, background-color .2s ease;
  }
  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 2px 8px rgba(200,200,255,0.28);
    background-color: rgba(200,200,255,0.3);
  }

  a {
    color: #7A6CEC !important;
    font-weight: 600;
    text-decoration: none;
    transition: color .15s ease, text-decoration-color .15s ease;
  }
  a:hover { color: #5E50D2 !important; text-decoration: underline; }

  #contact {
    background: var(--glass-bg);
    padding: 1.6rem;
    border-radius: 12px;
    margin-top: 2rem;
    box-shadow: 0 2px 10px rgba(200,200,255,0.16);
    border: 1px solid var(--glass-brd);
  }
  #contact p { color: var(--ink-2) !important; margin-bottom: .8rem; }

  @media (max-width: 640px) {
    main { margin: 20px auto; padding: 16px; border-radius: 14px; }
    th, td { padding: 10px 12px; }
  }
</style>

<script>
  function createStars() {
    const starsCount = 20;
    for (let i = 0; i < starsCount; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      star.style.left = Math.random() * 100 + 'vw';
      star.style.top = Math.random() * 100 + 'vh';
      star.style.animationDuration = (Math.random() * 28 + 24) + 's';
      star.style.animationDelay = (Math.random() * 10) + 's';
      document.body.appendChild(star);
    }
  }
  window.addEventListener('load', createStars);
</script>

<main>
  <h3>Me and Team</h3>
  <p>Hi! My name is Meryl.</p>

  <table>
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

  <h2>Links to Learning</h2>

  <h3>Development Environment</h3>
  <blockquote>
    <p>Coding starts with tools, explore these tools and procedures with a click.</p>
  </blockquote>

  <a href="https://github.com/Open-Coding-Society/student" class="badge" aria-label="GitHub Repository">
    <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub">
  </a>
  <a href="https://open-coding-society.github.io/student" class="badge" aria-label="GitHub Pages">
    <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?logo=github&logoColor=white" alt="GitHub Pages">
  </a>
  <a href="https://kasm.opencodingsociety.com/" class="button small">KASM</a>
  <a href="https://vscode.dev/" class="button small">VSCODE</a>

  <br><br>

  <h3>Class Progress</h3>
  <a href="{{site.baseurl}}/snake" class="button small">Snake Game</a>
  <a href="{{site.baseurl}}/turtle" class="button small">Turtle</a>

  <br><br>

  <div id="contact">
    <h3>Get in Touch</h3>
    <blockquote>
      <p>Feel free to reach out if you'd like to collaborate or learn more about our work.</p>
    </blockquote>
    <p>Open Coding Society: <a href="https://opencodingsociety.com">Socials</a></p>
  </div>
</main>
