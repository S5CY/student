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
            ribbon: "🇨🇳 China (1 year)",
            theme: "china",
            sticker: "🥟",
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
        launchEmojiConfetti(["🎉","✨","🎊","🌟","💫","🎈"]);
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
                animation: `fall ${Math.random()*1+1.9}s cubic-bezier(.2,.8,.2,1) forwards`
            });
            document.body.appendChild(span);
            setTimeout(()=> span.remove(), 2500);
        }
    }

    const styleFall = document.createElement("style");
    styleFall.textContent = `
      @keyframes fall{
        0%{ transform: translateY(0) rotate(0deg); opacity: 0; }
        10%{ opacity: 1; }
        100%{ transform: translateY(110vh) rotate(360deg); opacity: 0; }
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
            sticker: "🧩",
            chip: "Grade: 5"
        }
    ];

    var familyContainer = document.getElementById("family_container");
    family_members.forEach(member => {
        // 复用 makeCard，并把标题行用 role 填到第一行
        const card = makeCard({
            flag: member.flag,
            greeting: member.role,            // 放到第二行
            description: member.description,  // 放到第一行粗体
            ribbon: member.ribbon,
            theme: member.theme,
            sticker: member.sticker,
            chip: member.chip
        });
        // 交换两段文字，让 description 粗体在上、role 在下更合理
        const ps = card.querySelectorAll("p");
        if(ps.length >= 2){
            const strong = ps[0].textContent;
            ps[0].textContent = member.role;        // 第一行粗体显示角色
            ps[1].textContent = member.description; // 第二行显示描述
        }
        familyContainer.appendChild(card);
    });
</script>

<!-- ========= Fancy Dancing Cat (colored + detailed) ========= -->
<style>
  /* 容器定位在右下角 */
  .fx-cat-wrap {
    position: fixed;
    right: 20px;
    bottom: 20px;
    width: 140px;  /* 你可以调大/调小 */
    height: 180px;
    z-index: 9999;
    cursor: pointer;
    user-select: none;
  }

  /* 整体舞动：轻微上下律动 + 左右摆 */
  .fx-cat-svg {
    width: 100%;
    height: 100%;
    transform-origin: 50% 90%;
    animation: fx-cat-bop 1.6s ease-in-out infinite;
    filter: drop-shadow(0 6px 14px rgba(0,0,0,.25));
  }
  @keyframes fx-cat-bop {
    0%   { transform: translateY(0) rotate(-3deg); }
    50%  { transform: translateY(-6px) rotate(3deg); }
    100% { transform: translateY(0) rotate(-3deg); }
  }

  /* 尾巴左右摆动 */
  .fx-tail {
    transform-origin: 80px 120px; /* 与路径坐标对应的近似枢轴点 */
    animation: fx-tail-swing 0.9s ease-in-out infinite alternate;
  }
  @keyframes fx-tail-swing {
    from { transform: rotate(18deg); }
    to   { transform: rotate(-22deg); }
  }

  /* 前爪挥舞（左右互相错相） */
  .fx-paw-left {
    transform-origin: 38px 84px;
    animation: fx-paw-wave 0.8s ease-in-out infinite alternate;
  }
  .fx-paw-right {
    transform-origin: 82px 84px;
    animation: fx-paw-wave 0.8s ease-in-out infinite alternate-reverse;
  }
  @keyframes fx-paw-wave {
    from { transform: rotate(12deg); }
    to   { transform: rotate(-16deg); }
  }

  /* 耳朵轻微抖动（很小幅度） */
  .fx-ears {
    transform-origin: 60px 28px;
    animation: fx-ear-twitch 2.8s ease-in-out infinite;
  }
  @keyframes fx-ear-twitch {
    0%, 92%, 100% { transform: rotate(0deg); }
    94% { transform: rotate(-4deg); }
    96% { transform: rotate(4deg); }
    98% { transform: rotate(-2deg); }
  }

  /* 眼睛眨眼：用遮罩高度变化实现 */
  .fx-eye-mask {
    animation: fx-blink 4.2s infinite;
    transform-origin: 0 0;
  }
  @keyframes fx-blink {
    0%, 92%, 100% { transform: scaleY(1); }
    94% { transform: scaleY(0.15); }
    96% { transform: scaleY(1); }
  }

  /* 腿部轻微摆动（制造节奏感） */
  .fx-legs {
    transform-origin: 60px 150px;
    animation: fx-legs-step 1.6s ease-in-out infinite;
  }
  @keyframes fx-legs-step {
    0%   { transform: translateX(-1px) rotate(-1deg); }
    50%  { transform: translateX(1px) rotate(1deg); }
    100% { transform: translateX(-1px) rotate(-1deg); }
  }

  /* 脚下投影：随节奏缩放 */
  .fx-shadow {
    transform-origin: 60px 170px;
    animation: fx-shadow-pulse 1.6s ease-in-out infinite;
    opacity: .35;
  }
  @keyframes fx-shadow-pulse {
    0%   { transform: scaleX(1);   opacity: .35; }
    50%  { transform: scaleX(1.12); opacity: .22; }
    100% { transform: scaleX(1);   opacity: .35; }
  }

  /* 可选：点击切换“彩色项圈光泽” */
  .fx-cat-wrap:active .fx-collar-gloss {
    opacity: .9;
  }
</style>

<div class="fx-cat-wrap" title="meow~">
  <svg class="fx-cat-svg" viewBox="0 0 120 180" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <!-- ① 背景光晕（柔和） -->
    <defs>
      <radialGradient id="fx-bg-glow" cx="50%" cy="40%" r="70%">
        <stop offset="0%"  stop-color="#ffffff" stop-opacity="0.25"/>
        <stop offset="100%" stop-color="#9fd9ff" stop-opacity="0.0"/>
      </radialGradient>

      <!-- 毛色渐变（主色：奶油橘） -->
      <linearGradient id="fx-fur" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#f7c88a"/>
        <stop offset="100%" stop-color="#e6a96e"/>
      </linearGradient>

      <!-- 肚皮浅色 -->
      <linearGradient id="fx-belly" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#fff3e2"/>
        <stop offset="100%" stop-color="#ffe5c7"/>
      </linearGradient>

      <!-- 耳朵内侧粉 -->
      <linearGradient id="fx-ear-inner" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#ffc7d6"/>
        <stop offset="100%" stop-color="#f8a9bf"/>
      </linearGradient>

      <!-- 项圈红 + 高光 -->
      <linearGradient id="fx-collar" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#ff4b5c"/>
        <stop offset="100%" stop-color="#ff7a4a"/>
      </linearGradient>
      <linearGradient id="fx-collar-gloss-grad" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#ffffff" stop-opacity="0.7"/>
        <stop offset="100%" stop-color="#ffffff" stop-opacity="0"/>
      </linearGradient>

      <!-- 眨眼遮罩（矩形高度变化） -->
      <mask id="fx-eye-mask">
        <rect class="fx-eye-mask" x="0" y="0" width="120" height="180" fill="#fff"/>
      </mask>

      <!-- 条纹路径用的描边样式 -->
      <style>
        .fx-stripe { stroke:#d58640; stroke-width:3; stroke-linecap:round; fill:none; }
      </style>
    </defs>

    <!-- 背景光晕 -->
    <circle cx="60" cy="70" r="62" fill="url(#fx-bg-glow)"/>

    <!-- ② 脚下投影 -->
    <ellipse class="fx-shadow" cx="60" cy="168" rx="24" ry="6" fill="#000"/>

    <!-- ③ 尾巴（长而细，带浅色尖端） -->
    <g class="fx-tail">
      <path d="M78 118 
               C 100 110, 112 118, 108 138
               C 106 148, 94 150, 90 140
               C 88 135, 88 130, 80 125
               Z" 
            fill="url(#fx-fur)" opacity="0.95"/>
      <!-- 尾巴轮廓线 -->
      <path d="M78 118 
               C 100 110, 112 118, 108 138
               C 106 148, 94 150, 90 140
               C 88 135, 88 130, 80 125" 
            fill="none" stroke="#3b2c22" stroke-width="2"/>
      <!-- 尾尖浅色 -->
      <path d="M100 140
               C 102 142, 96 146, 92 142
               C 95 140, 97 139, 100 140 Z"
            fill="#ffe5c7" opacity="0.8"/>
    </g>

    <!-- ④ 身体（细长），含肚皮、条纹 -->
    <g class="fx-body">
      <!-- 主体 -->
      <path d="M40 70 
               Q 60 58, 80 70
               C 86 96, 84 126, 60 146
               C 36 126, 34 96, 40 70 Z"
            fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="2"/>

      <!-- 肚皮浅色 -->
      <path d="M52 78 
               Q 60 72, 68 78
               C 72 98, 70 120, 60 132
               C 50 120, 48 98, 52 78 Z"
            fill="url(#fx-belly)" opacity="0.95"/>

      <!-- 身体条纹 -->
      <path class="fx-stripe" d="M48 94 L40 90"/>
      <path class="fx-stripe" d="M50 106 L41 102"/>
      <path class="fx-stripe" d="M72 94 L80 90"/>
      <path class="fx-stripe" d="M70 108 L79 104"/>
    </g>

    <!-- ⑤ 头部（尖耳朵、脸部、胡须） -->
    <g class="fx-head">
      <!-- 头轮廓（稍微椭圆） -->
      <ellipse cx="60" cy="44" rx="18" ry="20" fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="2"/>

      <!-- 耳朵（尖且高） -->
      <g class="fx-ears">
        <path d="M42 24 L50 34 L48 10 Z" fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="2"/>
        <path d="M78 24 L70 34 L72 10 Z" fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="2"/>
        <!-- 耳朵内侧 -->
        <path d="M45 22 L50 34 L49 14 Z" fill="url(#fx-ear-inner)"/>
        <path d="M75 22 L70 34 L71 14 Z" fill="url(#fx-ear-inner)"/>
      </g>

      <!-- 眼睛（用遮罩实现眨眼） -->
      <g mask="url(#fx-eye-mask)">
        <ellipse cx="53" cy="42" rx="2.6" ry="3.2" fill="#1f1f1f"/>
        <ellipse cx="67" cy="42" rx="2.6" ry="3.2" fill="#1f1f1f"/>
        <!-- 高光点 -->
        <circle cx="52.2" cy="41.2" r="0.8" fill="#fff" opacity=".9"/>
        <circle cx="66.2" cy="41.2" r="0.8" fill="#fff" opacity=".9"/>
      </g>

      <!-- 鼻子 + 嘴 -->
      <path d="M58 48 Q60 50 62 48" fill="#e88" stroke="#3b2c22" stroke-width="1.2"/>
      <path d="M60 50
               c -2 1 -4 3 -4 5
               m 4 -5
               c 2 1 4 3 4 5" 
            stroke="#3b2c22" stroke-width="1.2" fill="none" stroke-linecap="round"/>

      <!-- 胡须 -->
      <path d="M46 48 L36 47" stroke="#3b2c22" stroke-width="1.6" stroke-linecap="round"/>
      <path d="M46 51 L35 52" stroke="#3b2c22" stroke-width="1.6" stroke-linecap="round"/>
      <path d="M74 48 L84 47" stroke="#3b2c22" stroke-width="1.6" stroke-linecap="round"/>
      <path d="M74 51 L85 52" stroke="#3b2c22" stroke-width="1.6" stroke-linecap="round"/>
    </g>

    <!-- ⑥ 项圈与小铃铛 -->
    <g class="fx-collar">
      <path d="M45 64 C 54 62, 66 62, 75 64" fill="none" stroke="url(#fx-collar)" stroke-width="6" stroke-linecap="round"/>
      <ellipse class="fx-collar-gloss" cx="60" cy="63" rx="26" ry="6" fill="url(#fx-collar-gloss-grad)" opacity=".65"/>
      <!-- 小铃铛 -->
      <circle cx="60" cy="66" r="4.2" fill="#ffd45c" stroke="#a87b1f" stroke-width="1.5"/>
      <line x1="60" y1="66" x2="60" y2="68.8" stroke="#a87b1f" stroke-width="1.4" stroke-linecap="round"/>
    </g>

    <!-- ⑦ 前爪（细长） -->
    <g class="fx-paw-left">
      <line x1="52" y1="84" x2="34" y2="66" stroke="#3b2c22" stroke-width="3" stroke-linecap="round"/>
      <path d="M34 66 Q 31 64, 28 66 Q 31 70, 34 66 Z" fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="1.5"/>
    </g>
    <g class="fx-paw-right">
      <line x1="68" y1="84" x2="86" y2="66" stroke="#3b2c22" stroke-width="3" stroke-linecap="round"/>
      <path d="M86 66 Q 89 64, 92 66 Q 89 70, 86 66 Z" fill="url(#fx-fur)" stroke="#3b2c22" stroke-width="1.5"/>
    </g>

    <!-- ⑧ 后腿（细长） -->
    <g class="fx-legs">
      <path d="M54 146 L48 164" stroke="#3b2c22" stroke-width="3" stroke-linecap="round"/>
      <path d="M66 146 L72 164" stroke="#3b2c22" stroke-width="3" stroke-linecap="round"/>
      <!-- 爪垫（小点装饰） -->
      <circle cx="46.5" cy="165.5" r="1.4" fill="#3b2c22" opacity=".8"/>
      <circle cx="73.5" cy="165.5" r="1.4" fill="#3b2c22" opacity=".8"/>
    </g>
  </svg>
</div>
<!-- ========= /Fancy Dancing Cat ========= -->
