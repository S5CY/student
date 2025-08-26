---
layout: post
title: About
permalink: /about/
comments: true
---

## 🌍 As a Conversation Starter

Here are some places I have lived.

<style>
    :root{
        --radius: 12px;
        --shadow: 0 4px 10px rgba(0,0,0,0.10);
        --shadow-lg: 0 12px 30px rgba(0,0,0,0.18);
        --text: #222;
        --text-strong: #111;
        --ribbon-grad: linear-gradient(90deg,rgb(255, 77, 169),rgb(123, 28, 255),rgb(46, 196, 194));
    }

    /* 背景：柔和漂浮色块 */
    body::before{
        content:"";
        position: fixed;
        inset:-20vmax;
        background:
            radial-gradient(40vmax 40vmax at 20% 30%, rgba(120,160,255,.25), transparent 60%),
            radial-gradient(45vmax 45vmax at 80% 20%, rgba(255,120,200,.22), transparent 60%),
            radial-gradient(35vmax 35vmax at 60% 80%, rgba(120,255,230,.20), transparent 60%);
        filter: blur(30px);
        z-index:-1;
        animation: floatBg 18s linear infinite alternate;
    }
    @keyframes floatBg{
        to{ transform: translateY(-2%) translateX(2%) scale(1.02); }
    }

    /* 顶部操作区 */
    .toolbar{
        display:flex; gap:10px; align-items:center; margin:10px 0 0;
    }
    .btn{
        border:0; border-radius: 999px; padding:10px 14px; font-size:.9rem; cursor:pointer;
        background: linear-gradient(135deg,#111,#333); color:#fff; box-shadow: var(--shadow);
        transition: transform .15s ease, box-shadow .15s ease, opacity .15s ease;
        user-select:none;
    }
    .btn:hover{ transform: translateY(-2px); box-shadow: var(--shadow-lg); }
    .btn:active{ transform: translateY(0); opacity:.85; }

    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
        gap: 22px;
        margin-top: 16px;
    }

    .grid-item {
        position: relative;
        border-radius: var(--radius);
        box-shadow: var(--shadow);
        text-align: center;
        padding: 16px 16px 18px;
        overflow: hidden;
        transform-style: preserve-3d;
        transition: transform 200ms ease, box-shadow 200ms ease, filter 200ms ease;
        will-change: transform;
        isolation: isolate;
    }
    .grid-item:hover {
        transform: translateY(-4px) rotateX(2deg) rotateY(-2deg);
        box-shadow: var(--shadow-lg);
    }

    /* 不同主题的卡片背景（自动适配） */
    .grid-item[data-theme="usa"],
    .grid-item[data-theme="california"]{
        background: linear-gradient(135deg, rgb(124,170,255), rgb(51,153,255));
    }
    .grid-item[data-theme="china"]{
        background: linear-gradient(135deg, rgb(222,41,16), rgb(255,115,80));
    }
    .grid-item[data-theme="neutral"]{
        background: linear-gradient(135deg, #f0f0f3, #e5e7eb);
    }

    /* 高光扫光效果 */
    .grid-item::after{
        content:"";
        position:absolute; inset:0;
        background: linear-gradient(120deg, transparent 30%, rgba(255,255,255,.18) 50%, transparent 70%);
        transform: translateX(-120%) skewX(-10deg);
        transition: transform .6s ease;
        pointer-events:none; z-index:0;
    }
    .grid-item:hover::after{ transform: translateX(120%) skewX(-10deg); }

    .grid-item img {
        width: 100%;
        height: 120px;
        object-fit: contain;
        border-radius: 10px;
        transition: transform 0.3s ease;
        background: transparent;
        z-index:1; position: relative;
    }
    .grid-item img:hover { transform: scale(1.05); }

    .grid-item p {
        margin: 10px 0 5px;
        font-size: 0.98rem;
        color: var(--text);
        z-index:1; position: relative;
    }
    .grid-item p:first-of-type {
        font-weight: 700;
        color: var(--text-strong);
    }

    /* 彩带 */
    .ribbon {
        position: absolute;
        top: 12px; left: -44px;
        width: 170px;
        text-align: center;
        line-height: 26px;
        font-size: 0.82rem;
        font-weight: 800;
        letter-spacing: .2px;
        color: white;
        transform: rotate(-45deg);
        background: var(--ribbon-grad);
        box-shadow: 0 2px 6px rgba(0,0,0,0.25);
        animation: ribbonWave 3s infinite ease-in-out;
        z-index:2;
        text-shadow: 0 1px 1px rgba(0,0,0,.25);
    }
    @keyframes ribbonWave {
        0%, 100% { transform: rotate(-45deg) translateY(0); }
        50% { transform: rotate(-45deg) translateY(3px); }
    }

    /* 可爱贴纸角标 */
    .sticker{
        position:absolute; right:8px; top:8px; font-size:22px; filter: drop-shadow(0 2px 4px rgba(0,0,0,.25));
        z-index:2;
    }

    /* 小标签（年限/身份） */
    .chip{
        display:inline-block; padding:4px 10px; border-radius:999px; font-size:.78rem; font-weight:600;
        background: rgba(255,255,255,.65); backdrop-filter: blur(4px);
        box-shadow: 0 2px 6px rgba(0,0,0,.08);
        margin-top:6px;
    }

    @media (max-width: 600px) {
        .grid-item{ padding: 12px; }
        .grid-item img{ height: 100px; }
    }
</style>

<!-- 顶部按钮：庆祝彩带 -->
<div class="toolbar">
    <button class="btn" id="celebrateBtn">🎊 Celebrate</button>
</div>

<div class="grid-container" id="grid_container"></div>

<script>
    // ====== 数据 ======
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {
            flag: "0/01/Flag_of_California.svg",
            greeting: "Hi 👋",
            description: "California — forever",
            ribbon: "🏠 Home",
            theme: "california",
            sticker: "🌴",
            chip: "Years: many"
        },
        {
            flag: "f/fa/Flag_of_the_People%27s_Republic_of_China.svg",
            greeting: "你好 👋",
            description: "China — 1 year",
            ribbon: "🇨🇳 1 year",
            theme: "china",
            sticker: "🥠",
            chip: "Years: 1"
        }
    ];

    // ====== 工具函数：生成卡片 ======
    function makeCard({flag,greeting,description,ribbon,theme="neutral",sticker="✨",chip=""}){
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";
        gridItem.setAttribute("data-theme", theme);

        var ribbonEl = document.createElement("div");
        ribbonEl.className = "ribbon";
        ribbonEl.textContent = ribbon;

        var stickerEl = document.createElement("div");
        stickerEl.className = "sticker";
        stickerEl.textContent = sticker;

        var img = document.createElement("img");
        img.src = http_source + flag;
        img.alt = description + " Flag";

        var desc = document.createElement("p");
        desc.textContent = description;

        var greet = document.createElement("p");
        greet.textContent = greeting;

        gridItem.appendChild(ribbonEl);
        gridItem.appendChild(stickerEl);
        gridItem.appendChild(img);
        gridItem.appendChild(desc);
        gridItem.appendChild(greet);

        if(chip){
            var chipEl = document.createElement("div");
            chipEl.className = "chip";
            chipEl.textContent = chip;
            gridItem.appendChild(chipEl);
        }
        return gridItem;
    }

    // ====== 渲染地点 ======
    var container = document.getElementById("grid_container");
    living_in_the_world.forEach(item => container.appendChild(makeCard(item)));

    // ====== 轻量彩带（表情）动画 ======
    var celebrateBtn = document.getElementById("celebrateBtn");
    celebrateBtn.addEventListener("click", () => {
        launchEmojiConfetti(["🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟""🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟""🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟""🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟""🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟""🎉","✨","🎊","🌟","💫","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟","💫","🌟","🎉","✨","🎊","🌟"]);
    });

    function launchEmojiConfetti(emojis){
        const burstCount = 26;
        for(let i=0;i<burstCount;i++){
            const span = document.createElement("span");
            span.textContent = emojis[Math.floor(Math.random()*emojis.length)];
            Object.assign(span.style,{
                position:"fixed",
                left: Math.random()*100+"vw",
                top: "-10vh",
                fontSize: (Math.random()*18+14)+"px",
                transform: `rotate(${(Math.random()*40-20)}deg)`,
                pointerEvents:"none",
                zIndex: 9999,
                filter: "drop-shadow(0 2px 3px rgba(0,0,0,.25))",
                animation: `fall ${Math.random()*1+2.5}s cubic-bezier(.2,.8,.2,1) forwards`
            });
            document.body.appendChild(span);
            setTimeout(()=> span.remove(), 4000);
        }
    }

    // 新版 fall 动画：落到底 → 停留 → 再消失
    const styleFall = document.createElement("style");
    styleFall.textContent = `
      @keyframes fall{
        0%   { transform: translateY(0) rotate(0deg); opacity: 0; }
        10%  { opacity: 1; }
        80%  { transform: translateY(100vh) rotate(340deg); opacity: 1; }
        95%  { transform: translateY(100vh) rotate(360deg); opacity: 1; }
        100% { transform: translateY(100vh) rotate(380deg); opacity: 0; }
      }
    `;
    document.head.appendChild(styleFall);
</script>

---

## 🚶 Journey through Life

Here is what I did at those places:

- 🏫 MR Elementary School in SD – 5 years  
- 🏫 OV Middle School in SD – 2 years  
- 🏫 Dipont School of Arts and Science in HZ – 1 year  
- 🏫 Del Norte High School in SD – '28  

---

## 👨‍👩‍👧 Family

Here are my family members:

<div class="grid-container" id="family_container"></div>

<script>
    // Family 数据
    var family_members = [
        {
            flag: "f/fa/Flag_of_the_People%27s_Republic_of_China.svg",
            role: "Dad",
            description: "Born in China",
            ribbon: "👨 Dad",
            theme: "china",
            sticker: "🧧",
            chip: "From CN"
        },
        {
            flag: "f/fa/Flag_of_the_People%27s_Republic_of_China.svg",
            role: "Mom",
            description: "Born in China",
            ribbon: "👩 Mom",
            theme: "china",
            sticker: "🌸",
            chip: "From CN"
        },
        {
            flag: "0/01/Flag_of_California.svg",
            role: "Sister",
            description: "Born in USA, now in 5th grade",
            ribbon: "👧 Sister",
            theme: "usa",
            sticker: "👹",
            chip: "Grade: 5"
        }
    ];

    var familyContainer = document.getElementById("family_container");
    family_members.forEach(member => {
        const card = makeCard({
            flag: member.flag,
            greeting: member.role,
            description: member.description,
            ribbon: member.ribbon,
            theme: member.theme,
            sticker: member.sticker,
            chip: member.chip
        });
        const ps = card.querySelectorAll("p");
        if(ps.length >= 2){
            ps[0].textContent = member.role;
            ps[1].textContent = member.description;
        }
        familyContainer.appendChild(card);
    });
</script>

<!-- ============================================================
     可爱的蟑螂 
=============================================================== -->
<style>
  .silly-roach-wrap{
    position: fixed;
    left: 20px;
    bottom: 20px;
    width: 120px;
    height: 180px;
    z-index: 9999;
    pointer-events: none; /* 不遮挡页面点击；需要交互改成 auto */
  }

  .silly-roach-svg{
    width: 100%;
    height: 100%;
    transform-origin: 50% 90%;
    animation: roach-bounce 2s ease-in-out infinite;
    filter: drop-shadow(0 4px 10px rgba(0,0,0,.25));
  }
  @keyframes roach-bounce{
    0%,100%{ transform: translateY(0); }
    50%    { transform: translateY(-6px); }
  }

  /* 头部整体左右轻摆；触角放在头部组里，随头一起转 */
  .roach-head{
    transform-origin: 60px 60px;
    animation: head-wobble 1.6s ease-in-out infinite;
  }
  @keyframes head-wobble{
    0%   { transform: rotate(-4deg); }
    50%  { transform: rotate(4deg); }
    100% { transform: rotate(-4deg); }
  }

  /* 触角微微柔性（很小幅度），不脱离头部节奏 */
  .roach-antenna{
    stroke: #222;
    stroke-width: 5;
    stroke-linecap: round;
    transform-origin: inherit;
    animation: antenna-flex 1.6s ease-in-out infinite;
  }
  @keyframes antenna-flex{
    0%,100%{ transform: rotate(0deg); }
    50%    { transform: rotate(3deg); }
  }

  /* 项圈+铃铛整组一起摆动 */
  .bell-group{
    transform-origin: 60px 96px; /* 挂点在项圈下沿附近 */
    animation: bell-swing 1.6s ease-in-out infinite;
  }
  @keyframes bell-swing{
    0%   { transform: rotate(-6deg); }
    50%  { transform: rotate(6deg); }
    100% { transform: rotate(-6deg); }
  }

  /* 细项圈（前半圈） */
  .collar-band{
    stroke: red;
    stroke-width: 4;
    stroke-linecap: round;
    fill: none;
  }

  /* 铃铛配色 */
  .roach-bell{
    fill: #ffd45c;
    stroke: #a87b1f;
    stroke-width: 2;
  }

  /* 肚皮淡色补丁 */
  .belly-patch{
    fill: #e7b994;
    opacity: .55;
  }
</style>

<div class="silly-roach-wrap" aria-hidden="true">
  <svg class="silly-roach-svg" viewBox="0 0 120 180" xmlns="http://www.w3.org/2000/svg">
    <!-- 身体 -->
    <ellipse cx="60" cy="102" rx="35" ry="56"
             fill="#a46b43" stroke="#222" stroke-width="6"/>
    <!-- 肚皮淡色补丁（更可爱） -->
    <ellipse class="belly-patch" cx="60" cy="118" rx="22" ry="30"/>

    <!-- 手 -->
    <line x1="45" y1="112" x2="56" y2="128" stroke="#222" stroke-width="6" stroke-linecap="round"/>
    <line x1="75" y1="112" x2="64" y2="128" stroke="#222" stroke-width="6" stroke-linecap="round"/>
    <!-- 腿 -->
    <line x1="48" y1="150" x2="48" y2="170" stroke="#222" stroke-width="6" stroke-linecap="round"/>
    <line x1="72" y1="150" x2="72" y2="170" stroke="#222" stroke-width="6" stroke-linecap="round"/>

    <!-- 头 + 触角（同组：一起摇） -->
    <g class="roach-head">
      <!-- 触角 -->
      <line class="roach-antenna" x1="45" y1="28" x2="25" y2="8"/>
      <line class="roach-antenna" x1="75" y1="28" x2="95" y2="8"/>
      <!-- 头 -->
      <ellipse cx="60" cy="60" rx="40" ry="34" fill="#c89062" stroke="#222" stroke-width="6"/>
      <!-- 眼睛 -->
      <circle cx="45" cy="56" r="5" fill="#222"/>
      <circle cx="75" cy="56" r="5" fill="#222"/>
      <!-- 嘴（微笑） -->
      <path d="M50 70 Q60 80 70 70"
            stroke="#222" stroke-width="5" fill="none" stroke-linecap="round"/>
    </g>

    <!-- 项圈（只画前半圈）+ 铃铛（整组摇摆） -->
    <g class="bell-group">
      <!-- 前半圈项圈：中心(60,92)，水平半径24，垂直半径10 -->
      <path class="collar-band"
            d="M 36 92 A 24 10 0 0 0 84 92"/>
      <!-- 链接线（跟组摆动） -->
      <line x1="60" y1="94" x2="60" y2="102"
            stroke="#a87b1f" stroke-width="3" stroke-linecap="round"/>
      <!-- 铃铛 -->
      <circle class="roach-bell" cx="60" cy="110" r="9"/>
      <line x1="60" y1="110" x2="60" y2="114"
            stroke="#a87b1f" stroke-width="2.5" stroke-linecap="round"/>
    </g>
  </svg>
</div>
