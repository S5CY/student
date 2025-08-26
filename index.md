---
layout: base
title: I'm Meryl
hide: true
---

<style>
  /* 统一柔和渐变背景 */
  body {
    color: #444;
    line-height: 1.6;
    transition: background-color 2s ease;
    animation: bgCycle 25s infinite alternate;
  }

  @keyframes bgCycle {
    0% { background: linear-gradient(135deg, #FFF0F5, #F0F8FF); }
    50% { background: linear-gradient(135deg, #F0FFF0, #FFF8F0); }
    100% { background: linear-gradient(135deg, #F5F0FF, #E6F9FF); }
  }

  /* 星星样式：更小更柔和 */
  .star {
    position: fixed;
    width: 2px;
    height: 2px;
    background: rgba(180,180,255,0.7);
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    animation: twinkle 2s infinite alternate, float 40s infinite linear;
  }
  
  @keyframes twinkle {
    0% { opacity: 0.4; transform: scale(0.6); }
    100% { opacity: 1; transform: scale(1); }
  }
  
  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    100% { transform: translate(80vw, 80vh) rotate(360deg); }
  }

  /* 标题样式 */
  h1, h2, h3, h4, h5, h6 {
    color: #6A5ACD !important;
    font-weight: 500;
  }

  /* 表格样式 */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.5rem 0;
    background: rgba(255,255,255,0.9);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(150,150,200,0.2);
  }
  
  th {
    background: linear-gradient(135deg, #B5C7EA, #C7B5EA);
    color: #FFF !important;
    padding: 12px;
    text-align: left;
    font-weight: 500;
    font-size: 0.85em;
    letter-spacing: 0.5px;
  }
  
  td {
    padding: 10px 14px;
    border-bottom: 1px solid #EEE;
    color: #555 !important;
    transition: all 0.2s ease;
  }
  
  tr:hover td {
    background-color: rgba(200,200,255,0.08);
    color: #6A5ACD !important;
  }

  /* 按钮样式 */
  .button.small {
    background: linear-gradient(135deg, #B5C7EA, #C7B5EA);
    border: none;
    color: white !important;
    font-weight: 500;
    padding: 8px 18px;
    border-radius: 20px;
    box-shadow: 0 2px 6px rgba(150, 130, 200, 0.3);
    transition: all 0.3s ease;
    margin: 0.2rem;
    text-decoration: none;
    display: inline-block;
  }
  
  .button.small:hover {
    background: linear-gradient(135deg, #A5B7DA, #B7A5DA);
    transform: translateY(-2px);
    box-shadow: 0 4px 10px rgba(150, 130, 200, 0.4);
  }

  /* 链接样式 */
  a {
    color: #7A6CEC !important;
    font-weight: 500;
    transition: all 0.2s ease;
    text-decoration: none;
  }
  
  a:hover {
    color: #5A4ACD !important;
    text-decoration: underline;
  }

  /* 联系方式 */
  #contact {
    background: rgba(255,255,255,0.95);
    padding: 1.5rem;
    border-radius: 12px;
    margin-top: 2.5rem;
    box-shadow: 0 2px 8px rgba(180,180,255,0.2);
    border: 1px solid rgba(220,220,255,0.5);
  }
  
  #contact p {
    color: #555 !important;
    margin-bottom: 0.8rem;
  }

  /* 徽章 */
  .badge {
    border-radius: 6px;
    padding: 2px 6px;
    display: inline-block;
    margin: 0.2rem;
    background-color: rgba(200,200,255,0.25);
    transition: all 0.3s ease;
  }
  
  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 2px 6px rgba(200,200,255,0.3);
  }
</style>

<script>
  // 柔和星星
  function createStars() {
    const starsCount = 20;
    for (let i = 0; i < starsCount; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      star.style.left = Math.random() * 100 + 'vw';
      star.style.top = Math.random() * 100 + 'vh';
      star.style.animationDuration = (Math.random() * 30 + 20) + 's';
      star.style.animationDelay = Math.random() * 10 + 's';
      document.body.appendChild(star);
    }
  }
  window.addEventListener('load', createStars);
</script>
