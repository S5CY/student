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
        launchEmojiConfetti(["🎉","✨","🎊","🌟","💫","🎈","✨","🌟","✨","✨","🌟","🌟","💫","🌟","🌟","✨","✨","💫","💫","✨","🌟","🌟","🌟","✨","💫","💫","✨","💫","✨","✨","💫","✨","✨"]);
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
            sticker: "👹",
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

<!-- ============================================================
     DC600 Dancing Cat (可爱版，黑白毛色 + 蓝绿眼)
=============================================================== -->
<style>
  :root{
    --dc600-fur-top: #2f3640;    /* 黑灰色 */
    --dc600-fur-bottom: #353b48;
    --dc600-belly-top: #ffffff;  /* 白肚皮 */
    --dc600-belly-bottom: #f1f2f6;
    --dc600-ear-inner-top: #ffc4d6; /* 粉耳内侧 */
    --dc600-ear-inner-bottom: #f39ac1;
    --dc600-stroke: #222;
    --dc600-eye-left: #00aaff;   /* 左眼 蓝色 */
    --dc600-eye-right: #00cc66;  /* 右眼 绿色 */
    --dc600-collar-left: #e84118;
    --dc600-collar-right: #fbc531;
    --dc600-bell: #ffd45c;
    --dc600-bell-stroke: #a87b1f;
    --dc600-shadow: rgba(0,0,0,.25);
  }

  .dc600-wrap{
    position: fixed;
    right: 20px;
    bottom: 20px;
    width: 160px;
    height: 200px;
    z-index: 9999;
    cursor: pointer;
  }

  .dc600-svg{
    width: 100%;
    height: 100%;
    filter: drop-shadow(0 6px 14px var(--dc600-shadow));
    transform-origin: 50% 90%;
    animation: dc600-bop 1.6s ease-in-out infinite;
  }
  @keyframes dc600-bop{
    0%   { transform: translateY(0) rotate(-2deg); }
    50%  { transform: translateY(-6px) rotate(2deg); }
    100% { transform: translateY(0) rotate(-2deg); }
  }

  .dc600-tail{
    transform-origin: 84px 126px;
    animation: dc600-tail-swing .9s ease-in-out infinite alternate;
  }
  @keyframes dc600-tail-swing{
    from{ transform: rotate(20deg); }
    to  { transform: rotate(-20deg); }
  }

  .dc600-paw-left{
    transform-origin: 40px 88px;
    animation: dc600-paw-wave .85s ease-in-out infinite alternate;
  }
  .dc600-paw-right{
    transform-origin: 80px 88px;
    animation: dc600-paw-wave .85s ease-in-out infinite alternate-reverse;
  }
  @keyframes dc600-paw-wave{
    from{ transform: rotate(12deg); }
    to  { transform: rotate(-18deg); }
  }

  .dc600-ears{
    transform-origin: 60px 30px;
    animation: dc600-ear-twitch 3s ease-in-out infinite;
  }
  @keyframes dc600-ear-twitch{
    0%, 92%, 100%{ transform: rotate(0deg); }
    94%{ transform: rotate(-4deg); }
    96%{ transform: rotate(4deg); }
    98%{ transform: rotate(-2deg); }
  }

  .dc600-eye-mask{
    animation: dc600-blink 4.5s infinite;
    transform-origin: 0 0;
  }
  @keyframes dc600-blink{
    0%, 94%, 100%{ transform: scaleY(1); }
    96% { transform: scaleY(.1); }
    98% { transform: scaleY(1); }
  }

  .dc600-shadow{
    transform-origin: 60px 182px;
    animation: dc600-shadow-pulse 1.6s ease-in-out infinite;
    opacity: .35;
  }
  @keyframes dc600-shadow-pulse{
    0%   { transform: scaleX(1);    opacity:.35; }
    50%  { transform: scaleX(1.12); opacity:.22; }
    100% { transform: scaleX(1);    opacity:.35; }
  }
</style>

<div class="dc600-wrap" title="cute kitty~">
  <svg class="dc600-svg" viewBox="0 0 120 200" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <!-- 脚下影子 -->
    <ellipse class="dc600-shadow" cx="60" cy="186" rx="26" ry="7" fill="#000"/>

    <!-- 尾巴 -->
    <g class="dc600-tail">
      <path d="M78 128 C 100 120, 112 128, 108 148 C 106 158, 96 160, 90 150 C 88 145, 86 138, 80 133 Z"
            fill="var(--dc600-fur-bottom)" stroke="var(--dc600-stroke)" stroke-width="2"/>
    </g>

    <!-- 身体 -->
    <g>
      <path d="M40 74 Q 60 60, 80 74 C 88 104, 86 134, 60 156 C 34 134, 32 104, 40 74 Z"
            fill="var(--dc600-fur-top)" stroke="var(--dc600-stroke)" stroke-width="2"/>
      <path d="M52 84 Q 60 76, 68 84 C 72 104, 70 128, 60 142 C 50 128, 48 104, 52 84 Z"
            fill="var(--dc600-belly-bottom)"/>
    </g>

    <!-- 头 -->
    <g class="dc600-head">
      <ellipse cx="60" cy="48" rx="20" ry="20" fill="var(--dc600-fur-top)" stroke="var(--dc600-stroke)" stroke-width="2"/>
      <g class="dc600-ears">
        <path d="M42 28 L51 38 L48 8 Z" fill="var(--dc600-fur-top)" stroke="var(--dc600-stroke)" stroke-width="2"/>
        <path d="M78 28 L69 38 L72 8 Z" fill="var(--dc600-fur-top)" stroke="var(--dc600-stroke)" stroke-width="2"/>
        <path d="M45 26 L51 38 L49 14 Z" fill="var(--dc600-ear-inner-bottom)"/>
        <path d="M75 26 L69 38 L71 14 Z" fill="var(--dc600-ear-inner-bottom)"/>
      </g>
      <!-- 左蓝眼 右绿眼 -->
      <g mask="url(#dc600-eye-mask)">
        <ellipse cx="53" cy="46" rx="3" ry="3.6" fill="var(--dc600-eye-left)"/>
        <ellipse cx="67" cy="46" rx="3" ry="3.6" fill="var(--dc600-eye-right)"/>
      </g>
      <!-- 鼻子和嘴巴 -->
      <circle cx="60" cy="52" r="2" fill="#e88"/>
      <path d="M60 54 c -2 2 -4 4 -4 6 m 4 -6 c 2 2 4 4 4 6"
            stroke="var(--dc600-stroke)" stroke-width="1.2" fill="none"/>
      <!-- 小胡须 -->
      <path d="M46 52 L34 51" stroke="var(--dc600-stroke)" stroke-width="1.5"/>
      <path d="M74 52 L86 51" stroke="var(--dc600-stroke)" stroke-width="1.5"/>
    </g>

    <!-- 项圈+铃铛 -->
    <g>
      <path d="M45 70 C 54 68, 66 68, 75 70"
            fill="none" stroke="url(#dc600-collar)" stroke-width="6" stroke-linecap="round"/>
      <circle cx="60" cy="72" r="5" fill="var(--dc600-bell)" stroke="var(--dc600-bell-stroke)" stroke-width="1.5"/>
    </g>

    <!-- 爪子 -->
    <g class="dc600-paw-left">
      <line x1="52" y1="88" x2="34" y2="68" stroke="var(--dc600-stroke)" stroke-width="3"/>
    </g>
    <g class="dc600-paw-right">
      <line x1="68" y1="88" x2="86" y2="68" stroke="var(--dc600-stroke)" stroke-width="3"/>
    </g>

    <!-- 腿 -->
    <g>
      <path d="M54 156 L48 176" stroke="var(--dc600-stroke)" stroke-width="3"/>
      <path d="M66 156 L72 176" stroke="var(--dc600-stroke)" stroke-width="3"/>
    </g>
  </svg>
</div>
