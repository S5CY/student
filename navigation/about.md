---
layout: post
title: About
permalink: /about/
comments: true
---

## 🌍 As a Conversation Starter

Here are some places I have lived.

<style>
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
        gap: 20px;
        margin-top: 20px;
    }

    .grid-item {
        position: relative;
        background: #fff;
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        text-align: center;
        padding: 15px;
        transition: transform 0.2s ease, box-shadow 0.2s ease;
        overflow: hidden;
    }

    .grid-item:hover {
        transform: translateY(-5px);
        box-shadow: 0 8px 18px rgba(0,0,0,0.15);
    }

    .grid-item img {
        width: 100%;
        height: 120px;
        object-fit: cover;
        border-radius: 8px;
        transition: transform 0.3s ease;
    }

    .grid-item img:hover {
        transform: scale(1.05);
    }

    .grid-item p {
        margin: 10px 0 5px;
        font-size: 0.95rem;
        color: #222; /* 深色文字，更清晰 */
    }

    .grid-item p:first-of-type {
        font-weight: bold;
        color: #111; /* 更深的黑色，用来突出描述 */
    }

    /* 彩带样式 */
    .ribbon {
        position: absolute;
        top: 12px;
        left: -40px;
        width: 160px;
        text-align: center;
        line-height: 24px;
        font-size: 0.8rem;
        font-weight: bold;
        color: white;
        transform: rotate(-45deg);
        background: linear-gradient(90deg, #ff4d6d, #ff9f1c, #2ec4b6);
        box-shadow: 0 2px 6px rgba(0,0,0,0.2);
        animation: ribbonWave 3s infinite ease-in-out;
    }

    @keyframes ribbonWave {
        0%, 100% { transform: rotate(-45deg) translateY(0); }
        50% { transform: rotate(-45deg) translateY(3px); }
    }

    @media (max-width: 600px) {
        .grid-item {
            padding: 10px;
        }
        .grid-item img {
            height: 100px;
        }
    }
</style>

<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    var container = document.getElementById("grid_container");

    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {
            "flag": "0/01/Flag_of_California.svg",
            "greeting": "Hi 👋",
            "description": "California - forever",
            "ribbon": "🏠 Home"
        },
        {
            "flag": "f/fa/Flag_of_the_People%27s_Republic_of_China.svg",
            "greeting": "你好 👋",
            "description": "China - 1 year",
            "ribbon": "🇨🇳 China (1 year)"
        }
    ];

    for (const location of living_in_the_world) {
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  

        // 彩带
        var ribbon = document.createElement("div");
        ribbon.className = "ribbon";
        ribbon.textContent = location.ribbon;

        var img = document.createElement("img");
        img.src = http_source + location.flag; 
        img.alt = location.flag + " Flag"; 

        var description = document.createElement("p");
        description.textContent = location.description; 

        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  

        gridItem.appendChild(ribbon);
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);
        container.appendChild(gridItem);
    }
</script>

---

### 🚶 Journey through Life

Here is what I did at those places:

- 🏫 MR Elementary School in SD – 5 years  
- 🏫 OV Middle School in SD – 2 years  
- 🏫 Dipont School of Arts and Science in HZ – 1 year  
- 🏫 Del Norte High School in SD – '28  
