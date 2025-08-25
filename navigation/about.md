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
        background: #fff;
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        text-align: center;
        padding: 15px;
        transition: transform 0.2s ease, box-shadow 0.2s ease;
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
        color: #444;
    }

    .grid-item p:first-of-type {
        font-weight: bold;
        color: #222;
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
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hi 👋", "description": "California - forever"},
    ];

    for (const location of living_in_the_world) {
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  

        var img = document.createElement("img");
        img.src = http_source + location.flag; 
        img.alt = location.flag + " Flag"; 

        var description = document.createElement("p");
        description.textContent = location.description; 

        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  

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
