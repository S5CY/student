---
layout: post
title: GitHub Pages
description: The Web Programming topics are focused on learning Frontend programming, GitHub Pages, and Jupyter Notebooks.
categories: ['JavaScript']
permalink: /github/pages/intro
type: ccc
courses: {'csse': {'week': 2}, 'csp': {'week': 2}, 'csa': {'week': 1}}
author: John Mortensen
menu: nav/github_pages.html
---

# GitHub Pages Mini Project

> Build a tiny, tasteful information site with a submenu and some playful interactivity.

This project helps you (and your pair) practice:
- Making a submenu
- Using submenu headings to guide subtopics
- Creating **custom pages** for each submenu
- Creating **data** and tracking information about your topic
- Adding **JavaScript actions** (buttons, forms, filters)
- Reviewing the anatomy and **Styles** of GitHub Pages
- Starting the process of **inspecting and debugging**

> **Tip:** Open DevTools to see `console.log` outputs.  
> VS Code → **Help → Toggle Developer Tools** → **Console** tab.

---

## Topics

Pick a topic you actually care about.

- Games: Discord groups, guides, mods, videos, avatar tips, etc.
- Fitness: training regimen, data tracking, prep (sleep, nutrition, water, calories, steps)
- Pets/Projects/Hobbies: anything that you can organize with subpages and little bits of data

---

## Brainstorm

- Gaming Blog  
- Fitness Blog  
- Raising Fish  
- Career Humor ✅ *(chosen for this example)*

---

## Brainwrite

The Teacher decided to create a mini project on **Career Humor**. As a Brainwrite activity, the Teacher brainstormed careers you could pursue from subjects taught at **Del Norte High School**.

### Brainwrite Submenu (Categories)

1. Computer Science
2. Accountant
3. Journalism
4. Film & Media
5. Mechanical Engineer
6. Biomedical Engineer
7. Astronomer

---

## Brainwrite Data (Career Humor)

Below is an **interactive joke explorer**.  
- Pick a **Category** → click **Random Joke**  
- Add your own joke + optional “complexity” or “effort” field  
- Your jokes are saved in **localStorage** (persist between reloads)  
- Filter the table; export your data as JSON

> **Note:** Some jokes include a light “complexity/effort” tag for fun (e.g., `O(1)`, “High Effort”). These are just flavor!

<style>
/* ---------- Page Polish ---------- */
:root{
  --bg: #0b1220;
  --panel: #0f172a;
  --ink: #e5e7eb;
  --muted: #94a3b8;
  --accent: #7c3aed;
  --accent-2: #22d3ee;
  --ok: #34d399;
  --warn: #fbbf24;
  --danger: #f87171;
  --ring: 0 0 0 3px rgba(124,58,237,.35);
}
@media (prefers-color-scheme: light){
  :root{
    --bg:#f8fafc; --panel:#ffffff; --ink:#0f172a; --muted:#475569;
    --accent:#6d28d9; --accent-2:#0891b2;
  }
}
*{box-sizing:border-box}
body{background:var(--bg); color:var(--ink)}
.post-content{font-size:1.05rem; line-height:1.7}
.card{
  background:var(--panel); border:1px solid rgba(148,163,184,.2);
  border-radius:16px; padding:1.1rem 1.2rem; box-shadow:0 10px 30px rgba(2,6,23,.25);
}
.grid{display:grid; gap:1rem}
.grid-2{grid-template-columns: repeat(2, minmax(0,1fr))}
@media (max-width:900px){ .grid-2{grid-template-columns:1fr} }
.hstack{display:flex; gap:.6rem; align-items:center}
.vstack{display:flex; gap:.6rem; flex-direction:column}
label{font-size:.9rem; color:var(--muted)}
input, select, textarea{
  width:100%; padding:.65rem .8rem; border-radius:12px;
  border:1px solid rgba(148,163,184,.35); background:transparent; color:var(--ink)
}
input:focus, select:focus, textarea:focus{ outline:none; box-shadow:var(--ring); border-color:var(--accent)}
button{
  border:0; padding:.7rem 1rem; border-radius:12px; cursor:pointer; font-weight:600
}
.btn{ background:linear-gradient(135deg, var(--accent), var(--accent-2)); color:white }
.btn.ghost{ background:transparent; color:var(--ink); border:1px solid rgba(148,163,184,.35) }
.btn.warn{ background:var(--warn); color:#111827 }
.btn.ok{ background:var(--ok); color:#052e1b }
.badge{
  font-size:.75rem; padding:.18rem .45rem; border-radius:999px;
  border:1px solid rgba(148,163,184,.4); color:var(--muted)
}
.table{
  width:100%; border-collapse:collapse; font-size:.95rem; overflow:auto
}
.table th, .table td{
  padding:.65rem .7rem; border-bottom:1px solid rgba(148,163,184,.25); vertical-align:top
}
.table th{ text-align:left; color:var(--muted); font-weight:700 }
.kbd{
  font-family: ui-monospace, SFMono-Regular, Menlo, monospace; 
  font-size:.85rem; padding:.15rem .35rem; border-radius:6px;
  background:rgba(148,163,184,.15); border:1px solid rgba(148,163,184,.35)
}
.small{ font-size:.9rem; color:var(--muted) }
.hr{ height:1px; background:linear-gradient(90deg, transparent, rgba(148,163,184,.35), transparent); margin:1rem 0 }
.callout{
  border-left:4px solid var(--accent); padding:.8rem 1rem; background:rgba(124,58,237,.08); border-radius:10px
}
.code-note{ font-family: ui-monospace, SFMono-Regular, Menlo, monospace; font-size:.9rem; color:var(--muted) }
</style>

<div class="grid grid-2">
  <div class="card vstack">
    <div class="hstack" style="justify-content:space-between">
      <div class="hstack" style="gap:.4rem">
        <span class="badge">Career Humor</span>
        <span class="badge" id="count-badge">0 jokes</span>
      </div>
      <button class="btn ghost" id="export-json" title="Export your current joke dataset">Export JSON</button>
    </div>

    <label for="category">Category</label>
    <select id="category">
      <option>Computer Science</option>
      <option>Accountant</option>
      <option>Journalism</option>
      <option>Film & Media</option>
      <option>Mechanical Engineer</option>
      <option>Biomedical Engineer</option>
      <option>Astronomer</option>
    </select>

    <div class="hstack" style="flex-wrap:wrap; gap:.5rem">
      <button class="btn" id="random-btn">🎲 Random Joke</button>
      <button class="btn ok" id="copy-btn" title="Copy last joke to clipboard">Copy Last</button>
      <button class="btn warn" id="clear-local" title="Remove user-added jokes">Clear My Added Jokes</button>
    </div>

    <div class="callout" id="joke-box" style="min-height:80px">
      <strong>Tip:</strong> Pick a category, then press <span class="kbd">Random Joke</span>.  
      New entries will appear here and in the table below.
    </div>

    <div class="hr"></div>

    <div class="vstack">
      <h3 style="margin:.2rem 0">Add Your Own Joke</h3>
      <label for="new-joke">Joke</label>
      <textarea id="new-joke" rows="3" placeholder="Type your joke…"></textarea>
      <div class="grid" style="grid-template-columns: 2fr 1fr">
        <div class="vstack">
          <label for="new-complexity">Complexity / Effort (optional)</label>
          <input id="new-complexity" placeholder='e.g., O(1), "High Effort", "Needs Coffee"'>
        </div>
        <div class="vstack">
          <label>&nbsp;</label>
          <button class="btn" id="add-joke">➕ Add Joke</button>
        </div>
      </div>
      <div class="small">Your added jokes are saved locally in <code class="code-note">localStorage</code>.</div>
    </div>
  </div>

  <div class="card vstack">
    <div class="hstack" style="justify-content:space-between">
      <h3 style="margin:0">Joke Data</h3>
      <div class="hstack">
        <label for="filter">Filter</label>
        <input id="filter" placeholder="Search joke, category, or complexity…">
      </div>
    </div>
    <div style="overflow:auto; border-radius:12px">
      <table class="table" id="joke-table">
        <thead>
          <tr>
            <th style="width:12rem">Category</th>
            <th>Joke</th>
            <th style="width:8rem">Complexity</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
    </div>
    <div class="small">Inspect console for logs when you click <span class="kbd">🎲 Random Joke</span>.</div>
  </div>
</div>

<div class="hr"></div>

## Notes on Files & Structure

### Key Locations for this Mini Project

- **`_includes`**  
  - Shared components across pages (e.g., submenu).  
  - In `portfolio_2025`, put submenu files here.  
  - Submenu path: **`_includes/nav/github_pages.html`** — contains a `<table>` with `<tr>`, `<td>`, and `<a>` tags for links.

- **`_notebooks`**  
  - Default home for your Jupyter **`.ipynb`** files.  
  - Files placed here are converted to pages by GitHub Pages Actions.  
  - Start by copying **`_notebooks/Foundations/C-github_pages`** to your project and modify as needed.

- In each notebook’s **front matter**:  
  - `menu: nav/github_pages.html` — includes the submenu  
  - `permalink: /github/pages/intro` — corresponds to an `<a>` in the submenu table

---

## Conversions & Energy (Reference Block)

<div class="card">
  <strong>Quick Conversions</strong>
  <div class="grid" style="grid-template-columns: repeat(3, minmax(0,1fr))">
    <div class="vstack small">
      <span>1 mi² = 640 acres</span>
      <span>1 acre = 0.405 hectares</span>
      <span>1 L = 0.264 gallons</span>
    </div>
    <div class="vstack small">
      <span>1 kWh = 3.4 × 10⁴ BTU</span>
      <span>≈ 8.6 × 10⁵ calories</span>
      <span>1 Mg = 10³ kg</span>
    </div>
    <div class="vstack small">
      <span>1 barrel oil = 42 gallons</span>
      <span>≈ 6 million BTUs</span>
    </div>
  </div>
</div>

---

<script>
/* ============================================================
   Career Humor Joke Engine
   - curated defaults per category
   - add-your-own jokes (localStorage)
   - random selection + table rendering + filter
   - console logging to practice debugging
   ============================================================ */

// ---------- Default Datasets ----------
const DEFAULT_JOKES = {
  "Computer Science": [
    { joke: "Why do programmers prefer dark mode? Because light attracts bugs.", complexity: "O(1)" },
    { joke: "There are 10 types of people: those who understand binary and those who don't.", complexity: "O(1)" },
    { joke: "I told my compiler a joke—now it won’t stop optimizing the punchline.", complexity: "O(log n)" },
    { joke: "My code works... on my machine. Must be a networking issue—intra-cranial.", complexity: "Heisenbug" },
    { joke: "Why did the function break up? It had too many arguments.", complexity: "O(n)" },
    { joke: "Java developers wear glasses because they don’t C#.", complexity: "O(1)" },
    { joke: "I would tell you a UDP joke, but you might not get it.", complexity: "Best-effort" },
    { joke: "I had a problem, so I used recursion. I had a problem, so I used recursion.", complexity: "O(∞)" },
    { joke: "Git commit—relationship status: ‘It’s complicated (HEAD detached)’", complexity: "Rebase needed" },
    { joke: "Oct 31 == Dec 25 for some programmers.", complexity: "Spooky math" }
  ],
  "Accountant": [
    { joke: "Why did the accountant cross the road? To reconcile both sides.", complexity: "Balanced" },
    { joke: "Accountant at the beach: working on tan lines and bottom lines.", complexity: "High Return" },
    { joke: "Accrual world: revenue today, feelings later.", complexity: "Matching Principle" },
    { joke: "I told my accountant a joke. She deferred the laughter to next period.", complexity: "Deferred Humor" },
    { joke: "Why are accountants calm? They’ve already seen all the figures.", complexity: "Materially Fair" },
    { joke: "Cash flow party: come as you are, leave as you were.", complexity: "Non-cash Expense" },
    { joke: "CPA motto: In numbers we trust; in pencils we verify.", complexity: "Double-Entry" }
  ],
  "Journalism": [
    { joke: "Journalist’s favorite HTML tag? <angle>—always looking for one.", complexity: "Low Effort" },
    { joke: "Editor to writer: Your lead is strong; your facts will follow later, right?", complexity: "Deadline Driven" },
    { joke: "Investigative reporter’s diet: lots of sources, no fluff.", complexity: "Primary Source" },
    { joke: "We don’t make typos—we publish limited editions.", complexity: "Correction Pending" }
  ],
  "Film & Media": [
    { joke: "Director: We’ll fix it in post. Post: We’ll fix the director.", complexity: "High Effort" },
    { joke: "Cinematographer’s mantra: If it’s out of focus, it’s art.", complexity: "Soft Focus" },
    { joke: "Boom operator’s nightmare: quiet actors, loud chairs.", complexity: "Pop Filter" },
    { joke: "Plot twist: the budget was the real antagonist.", complexity: "Producer’s Cut" }
  ],
  "Mechanical Engineer": [
    { joke: "If it moves and shouldn’t: duct tape. If it doesn’t and should: WD-40.", complexity: "O(1) toolkit" },
    { joke: "ME dating advice: reduce friction, increase support.", complexity: "Statics & Dynamics" },
    { joke: "We don’t make mistakes—just rapid prototyping.", complexity: "Rev B" },
    { joke: "Tolerance? ± pizza slice.", complexity: "Shop Floor Spec" }
  ],
  "Biomedical Engineer": [
    { joke: "Our MVP is a Minimum Viable Pacemaker.", complexity: "Heart-ware" },
    { joke: "CRISPR: when your edit history includes genomes.", complexity: "High Precision" },
    { joke: "Biomed wireframing? More like wire-lessing.", complexity: "FDA Pending" },
    { joke: "Wearables: because your cells forgot to send logs.", complexity: "Telemetry" }
  ],
  "Astronomer": [
    { joke: "Astronomers’ parties have stellar turnouts—space is never a problem.", complexity: "Universal" },
    { joke: "I asked for more space; they gave me a telescope.", complexity: "Expansion Pack" },
    { joke: "Black hole at work: great at taking feedback, never returns it.", complexity: "Event Horizon" },
    { joke: "Comet plans are like deadlines: they keep passing.", complexity: "Periodic" }
  ]
};

// ---------- Local Storage Keys ----------
const LS_KEY = "careerHumorUserJokes";

// ---------- State ----------
let lastShown = null;

// ---------- DOM ----------
const categorySel = document.getElementById("category");
const randomBtn    = document.getElementById("random-btn");
const jokeBox      = document.getElementById("joke-box");
const addBtn       = document.getElementById("add-joke");
const newJokeInput = document.getElementById("new-joke");
const newComplexityInput = document.getElementById("new-complexity");
const tableBody    = document.querySelector("#joke-table tbody");
const filterInput  = document.getElementById("filter");
const copyBtn      = document.getElementById("copy-btn");
const clearLocal   = document.getElementById("clear-local");
const exportBtn    = document.getElementById("export-json");
const countBadge   = document.getElementById("count-badge");

// ---------- Utilities ----------
function getUserJokes(){
  try{ return JSON.parse(localStorage.getItem(LS_KEY) || "{}"); }
  catch { return {}; }
}
function setUserJokes(data){
  localStorage.setItem(LS_KEY, JSON.stringify(data));
}
function getCombined(category){
  const base = DEFAULT_JOKES[category] || [];
  const user = getUserJokes()[category] || [];
  return [...base, ...user];
}
function updateCount(){
  let total = 0;
  Object.keys(DEFAULT_JOKES).forEach(cat => total += DEFAULT_JOKES[cat].length);
  const user = getUserJokes();
  Object.keys(user).forEach(cat => total += user[cat].length);
  countBadge.textContent = `${total} jokes`;
}

// ---------- Rendering ----------
function renderTable(){
  const query = filterInput.value.toLowerCase().trim();
  const rows = [];
  const cats = Object.keys(DEFAULT_JOKES);

  cats.forEach(cat=>{
    const items = getCombined(cat);
    items.forEach(({joke, complexity})=>{
      if(!query || [cat, joke, complexity||""].join(" ").toLowerCase().includes(query)){
        rows.push(`<tr>
          <td><span class="badge">${cat}</span></td>
          <td>${escapeHtml(joke)}</td>
          <td>${complexity ? `<span class="badge">${escapeHtml(complexity)}</span>` : ""}</td>
        </tr>`);
      }
    });
  });
  tableBody.innerHTML = rows.join("") || `<tr><td colspan="3" class="small">No matches.</td></tr>`;
  updateCount();
}

function escapeHtml(s){
  return (s||"").replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m]));
}

// ---------- Actions ----------
randomBtn.addEventListener("click", ()=>{
  const cat = categorySel.value;
  const list = getCombined(cat);
  if(list.length === 0){
    jokeBox.innerHTML = "No jokes yet—add one below!";
    return;
  }
  const idx = Math.floor(Math.random()*list.length);
  const picked = list[idx];
  lastShown = { ...picked, category: cat };
  const tag = picked.complexity ? ` <span class="badge">${escapeHtml(picked.complexity)}</span>` : "";
  jokeBox.innerHTML = `<strong>${escapeHtml(cat)}</strong>${tag}<br>${escapeHtml(picked.joke)}`;

  // Console practice
  console.log(`Joke #${idx+1} [${cat}] ->`, picked);
});

copyBtn.addEventListener("click", async ()=>{
  if(!lastShown){ alert("No joke to copy yet! Click Random Joke first."); return; }
  const text = `[${lastShown.category}] ${lastShown.joke}${lastShown.complexity ? " ("+lastShown.complexity+")" : ""}`;
  try{
    await navigator.clipboard.writeText(text);
    copyBtn.textContent = "Copied!";
    setTimeout(()=> copyBtn.textContent = "Copy Last", 1000);
  }catch(e){
    alert("Clipboard copy failed. You can select and copy manually.");
  }
});

addBtn.addEventListener("click", ()=>{
  const cat = categorySel.value;
  const text = newJokeInput.value.trim();
  const cx   = newComplexityInput.value.trim();

  if(!text){ alert("Please enter a joke first."); return; }

  const data = getUserJokes();
  data[cat] = data[cat] || [];
  data[cat].push({ joke: text, complexity: cx || undefined });
  setUserJokes(data);

  newJokeInput.value = "";
  newComplexityInput.value = "";
  renderTable();

  // also show it immediately
  lastShown = { joke: text, complexity: cx || undefined, category: cat };
  const tag = cx ? ` <span class="badge">${escapeHtml(cx)}</span>` : "";
  jokeBox.innerHTML = `<strong>${escapeHtml(cat)}</strong>${tag}<br>${escapeHtml(text)}`;
  console.log("Added user joke:", lastShown);
});

filterInput.addEventListener("input", renderTable);

clearLocal.addEventListener("click", ()=>{
  if(confirm("Remove all jokes you’ve added (keeps the defaults)?")){
    localStorage.removeItem(LS_KEY);
    renderTable();
  }
});

exportBtn.addEventListener("click", ()=>{
  const payload = {
    defaults: DEFAULT_JOKES,
    userAdded: getUserJokes()
  };
  const blob = new Blob([JSON.stringify(payload, null, 2)], { type: "application/json" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = "career_humor_jokes.json";
  document.body.appendChild(a);
  a.click();
  a.remove();
  URL.revokeObjectURL(url);
});

// ---------- Init ----------
renderTable();
updateCount();
</script>
