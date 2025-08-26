---
layout: base
title: I'm Meryl
hide: true
---

<style>
  :root{
    --ink:#dcdcef;               /* 浅灰紫文字 */
    --ink-2:#b5b5d0;
    --primary:#4A3FA6;           /* 深蓝紫 */
    --accent-1:#5c6ac4;          /* 蓝紫 */
    --accent-2:#7c5ac7;          /* 紫色 */
    --glass-bg: rgba(30,30,60,0.7);
    --glass-brd: rgba(100,100,150,0.4);
    --shadow: 0 8px 24px rgba(0,0,0,0.45);
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
    0%   { background: radial-gradient(1200px 800px at 10% 10%, #1f1b2e 0%, #2a2d4f 55%, #3b2d56 100%); }
    50%  { background: radial-gradient(1200px 800px at 90% 20%, #2c2f50 0%, #3b345c 60%, #26223d 100%); }
    100% { background: radial-gradient(1200px 800px at 50% 80%, #1e1e33 0%, #32294f 60%, #201d36 100%); }
  }

  .star {
    position: fixed;
    width: 2px;
    height: 2px;
    background: rgba(200, 200, 255, 0.7);
    border-radius: 50%;
    pointer-events: none;
    z-index: 1;
    animation: twinkle 2.2s infinite alternate ease-in-out, float 38s linear infinite;
  }
  @keyframes twinkle {
    0%   { opacity: .25; transform: scale(.6); }
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
    backdrop-filter: blur(8px);
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
    background: rgba(40,40,70,0.8);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 10px rgba(0,0,0,0.5);
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
    border-bottom: 1px solid rgba(255,255,255,0.1);
    color: #d0cdee !important;
    transition: background-color .2s ease, color .2s ease;
  }
  tr:last-child td { border-bottom: none; }
  tr:hover td {
    background-color: rgba(120,120,200,0.15);
    color: #fff !important;
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
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.5);
    transition: transform .2s ease, box-shadow .2s ease, filter .2s ease;
  }
  .button.small:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 18px rgba(0, 0, 0, 0.6);
    filter: brightness(1.1);
  }
  .badge {
    padding: 6px 10px;
    border-radius: 10px;
    background-color: rgba(100,100,160,0.3);
    color: var(--ink);
    font-weight: 600;
    transition: transform .2s ease, box-shadow .2s ease, background-color .2s ease;
  }
  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 2px 8px rgba(0,0,0,0.4);
    background-color: rgba(120,120,200,0.4);
  }

  a {
    color: #9c93ff !important;
    font-weight: 600;
    text-decoration: none;
    transition: color .15s ease;
  }
  a:hover { color: #cfcaff !important; }

  #contact {
    background: rgba(40,40,70,0.8);
    padding: 1.6rem;
    border-radius: 12px;
    margin-top: 2rem;
    box-shadow: 0 2px 10px rgba(0,0,0,0.5);
    border: 1px solid var(--glass-brd);
  }
  #contact p { color: var(--ink) !important; margin-bottom: .8rem; }

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

  <a href="https://github.com/Open-Coding-Society/student" class="badge">GitHub</a>
  <a href="https://open-coding-society.github.io/student" class="badge">GitHub Pages</a>
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
