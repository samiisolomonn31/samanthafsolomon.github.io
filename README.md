<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Samantha Solomon — Resume</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323&display=swap" rel="stylesheet"/>
<style>
  :root {
    --grass:    #5a9e3a;
    --grass2:   #4a8a2e;
    --dirt:     #c8956b;
    --dirt2:    #b07d52;
    --wood:     #8b5e3c;
    --wood2:    #6b4423;
    --sky:      #7ec8e3;
    --panel:    #f5e6c8;
    --panel2:   #e8d4a8;
    --border:   #5c3d1e;
    --text:     #3b2007;
    --gold:     #f0c040;
    --gold2:    #d4a017;
    --green:    #3a7d2c;
    --red:      #c0392b;
    --blue:     #2980b9;
    --heart:    #e74c3c;
    --star:     #f1c40f;
    --shadow:   #2c1a0e;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'VT323', monospace;
    background: var(--sky);
    color: var(--text);
    min-height: 100vh;
    cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16'%3E%3Crect x='6' y='0' width='4' height='16' fill='%235c3d1e'/%3E%3Crect x='0' y='6' width='16' height='4' fill='%235c3d1e'/%3E%3C/svg%3E") 8 8, crosshair;
    overflow-x: hidden;
  }

  /* ── ANIMATED SKY BG ── */
  .sky-bg {
    position: fixed; inset: 0; z-index: 0;
    background: linear-gradient(180deg, #87ceeb 0%, #b0e0f5 50%, #7ec8e3 100%);
  }

  /* Pixel clouds */
  .cloud {
    position: fixed; z-index: 0;
    width: 64px; height: 24px;
    background: white;
    image-rendering: pixelated;
    opacity: 0.85;
    animation: drift linear infinite;
  }
  .cloud::before, .cloud::after {
    content: ''; position: absolute;
    background: white;
  }
  .cloud::before { width: 32px; height: 16px; top: -10px; left: 8px; }
  .cloud::after  { width: 20px; height: 12px; top: -6px; left: 28px; }
  .cloud:nth-child(1) { top: 8%;  animation-duration: 40s; animation-delay: 0s; }
  .cloud:nth-child(2) { top: 15%; animation-duration: 55s; animation-delay: -20s; width: 80px; }
  .cloud:nth-child(3) { top: 5%;  animation-duration: 35s; animation-delay: -10s; width: 48px; }
  @keyframes drift { from { left: -100px; } to { left: 110%; } }

  /* Pixel grass ground */
  .ground {
    position: fixed; bottom: 0; left: 0; right: 0; height: 48px; z-index: 1;
    background: var(--grass);
    border-top: 8px solid var(--grass2);
  }
  .ground::before {
    content: '';
    position: absolute; top: -16px; left: 0; right: 0; height: 8px;
    background: repeating-linear-gradient(90deg, var(--grass2) 0 8px, var(--grass) 8px 16px);
  }

  /* ── LAYOUT ── */
  .page {
    position: relative; z-index: 2;
    max-width: 900px; margin: 0 auto;
    padding: -1rem 1.5rem 6rem;
  }

  /* ── NAMEPLATE / HEADER ── */
  .nameplate {
    background: var(--panel);
    border: 4px solid var(--border);
    box-shadow: 6px 6px 0 var(--shadow);
    padding: 1.5rem 2rem;
    margin-bottom: 1.5rem;
    position: relative;
    image-rendering: pixelated;
    animation: popIn 0.5s cubic-bezier(.36,1.56,.64,1) both;
  }
  @keyframes popIn {
    from { opacity:0; transform: scale(0.85) translateY(20px); }
    to   { opacity:1; transform: scale(1) translateY(0); }
  }

  .nameplate-inner {
    display: flex; gap: 1.5rem; align-items: flex-start; flex-wrap: wrap;
  }

  /* Pixel character sprite */
  .sprite {
    width: 64px; height: 80px; flex-shrink: 0;
    image-rendering: pixelated;
    position: relative;
  }
  .sprite canvas { image-rendering: pixelated; }

  .name-block { flex: 1; min-width: 200px; }

  .name-block h1 {
    font-family: 'Press Start 2P', monospace;
    font-size: clamp(0.9rem, 2.5vw, 1.4rem);
    color: var(--wood2);
    text-shadow: 2px 2px 0 var(--gold2);
    line-height: 1.4;
    margin-bottom: 0.4rem;
  }

  .job-title {
    font-size: 1.4rem;
    color: var(--green);
    margin-bottom: 0.6rem;
  }

  .contact-row {
    display: flex; flex-wrap: wrap; gap: 0.5rem;
    font-size: 1.1rem; color: var(--wood);
  }
  .contact-row a { color: var(--blue); text-decoration: none; }
  .contact-row a:hover { color: var(--red); }
  .contact-row span { color: var(--border); }

  /* Hearts / stars row */
  .stars-row { display: flex; gap: 4px; margin-top: 0.5rem; }
  .star { font-size: 1.2rem; color: var(--star); animation: twinkle 2s infinite; }
  .star:nth-child(2) { animation-delay: 0.3s; }
  .star:nth-child(3) { animation-delay: 0.6s; }
  .star:nth-child(4) { animation-delay: 0.9s; }
  .star:nth-child(5) { animation-delay: 1.2s; }
  @keyframes twinkle { 0%,100%{opacity:1;} 50%{opacity:0.4;} }

  /* ── SECTION PANEL ── */
  .panel {
    background: var(--panel);
    border: 4px solid var(--border);
    box-shadow: 6px 6px 0 var(--shadow);
    margin-bottom: 1.5rem;
    animation: popIn 0.5s cubic-bezier(.36,1.56,.64,1) both;
  }

  .panel-header {
    background: var(--wood);
    padding: 0.6rem 1rem;
    display: flex; align-items: center; gap: 0.6rem;
    cursor: pointer;
    user-select: none;
    transition: background 0.15s;
  }
  .panel-header:hover { background: var(--wood2); }

  .panel-header h2 {
    font-family: 'Press Start 2P', monospace;
    font-size: 0.7rem;
    color: var(--gold);
    text-shadow: 1px 1px 0 var(--shadow);
    flex: 1;
  }

  .panel-icon { font-size: 1.4rem; }

  .toggle-btn {
    font-family: 'Press Start 2P', monospace;
    font-size: 0.6rem;
    color: var(--gold);
    background: none; border: none; cursor: pointer;
    transition: transform 0.3s;
  }
  .toggle-btn.open { transform: rotate(180deg); }

  .panel-body {
    padding: 1.2rem 1.5rem;
    overflow: hidden;
    transition: max-height 0.4s ease, padding 0.3s ease;
  }
  .panel-body.collapsed { max-height: 0 !important; padding-top: 0; padding-bottom: 0; }

  /* ── SUMMARY ── */
  .summary-text {
    font-size: 1.35rem; line-height: 1.7;
    color: var(--text);
    background: var(--panel2);
    border: 2px solid var(--border);
    padding: 1rem;
    position: relative;
  }
  .summary-text::before {
    content: '💬';
    position: absolute; top: -14px; left: 12px;
    font-size: 1.4rem;
  }

  /* ── EXPERIENCE ── */
  .job-card {
    border: 3px solid var(--border);
    background: var(--panel2);
    margin-bottom: 1rem;
    transition: box-shadow 0.2s, transform 0.2s;
    cursor: pointer;
  }
  .job-card:hover {
    box-shadow: 4px 4px 0 var(--gold2);
    transform: translate(-2px, -2px);
  }
  .job-card:last-child { margin-bottom: 0; }

  .job-header {
    background: var(--dirt);
    padding: 0.5rem 0.8rem;
    display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 0.3rem;
    border-bottom: 2px solid var(--border);
  }
  .job-title-text {
    font-family: 'Press Start 2P', monospace;
    font-size: 0.55rem;
    color: var(--wood2);
  }
  .job-company {
    font-size: 1.1rem; color: var(--green); font-weight: bold;
  }
  .job-date {
    font-size: 1rem; color: var(--wood);
  }

  .job-body { padding: 0.8rem; overflow: hidden; transition: max-height 0.3s ease; }
  .job-body.collapsed { max-height: 0 !important; padding: 0; }

  .job-bullet {
    display: flex; gap: 0.5rem; align-items: flex-start;
    font-size: 1.15rem; line-height: 1.5;
    margin-bottom: 0.4rem; color: var(--text);
  }
  .job-bullet::before { content: '▸'; color: var(--green); flex-shrink: 0; margin-top: 1px; }

  /* ── SKILLS ── */
  .skills-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 0.8rem;
  }

  .skill-item {
    background: var(--panel2);
    border: 2px solid var(--border);
    padding: 0.5rem 0.7rem;
    display: flex; align-items: center; gap: 0.5rem;
    font-size: 1.1rem; line-height: 1.4;
    transition: transform 0.15s, box-shadow 0.15s;
    cursor: default;
  }
  .skill-item:hover {
    transform: translate(-2px, -2px);
    box-shadow: 3px 3px 0 var(--gold2);
  }
  .skill-item::before { content: '⚒️'; font-size: 1rem; flex-shrink: 0; }

  /* ── CERTS ── */
  .cert-list { display: flex; flex-direction: column; gap: 0.6rem; }

  .cert-item {
    background: var(--panel2);
    border: 2px solid var(--border);
    padding: 0.5rem 0.8rem;
    display: flex; align-items: center; gap: 0.6rem;
    font-size: 1.2rem;
    transition: transform 0.15s, box-shadow 0.15s;
    cursor: default;
  }
  .cert-item:hover {
    transform: translate(-2px, -2px);
    box-shadow: 3px 3px 0 var(--gold2);
  }
  .cert-badge {
    font-size: 1.4rem;
  }
  .cert-year {
    margin-left: auto;
    font-family: 'Press Start 2P', monospace;
    font-size: 0.5rem;
    color: var(--wood);
    background: var(--dirt);
    padding: 2px 6px;
    border: 1px solid var(--border);
  }

  /* ── EDUCATION ── */
  .edu-card {
    background: var(--panel2);
    border: 2px solid var(--border);
    padding: 1rem;
    display: flex; gap: 1rem; align-items: center; flex-wrap: wrap;
    font-size: 1.2rem;
  }
  .edu-icon { font-size: 2.5rem; }
  .edu-name {
    font-family: 'Press Start 2P', monospace;
    font-size: 0.6rem; color: var(--wood2);
    margin-bottom: 0.3rem;
  }
  .edu-degree { color: var(--green); }
  .edu-years  { color: var(--wood);  font-size: 1rem; }

  /* ── PIXEL ART CHARACTER (canvas) ── */
  #playerCanvas { display: block; }

  /* ── NOTIFICATION TOAST ── */
  #toast {
    position: fixed; bottom: 80px; left: 50%; transform: translateX(-50%) translateY(20px);
    background: var(--panel); border: 3px solid var(--border);
    box-shadow: 4px 4px 0 var(--shadow);
    padding: 0.6rem 1.2rem;
    font-family: 'Press Start 2P', monospace; font-size: 0.55rem;
    color: var(--text);
    z-index: 999; pointer-events: none;
    opacity: 0; transition: opacity 0.3s, transform 0.3s;
    white-space: nowrap;
  }
  #toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

  /* ── XP BAR ── */
  .xp-bar-wrap {
    margin-top: 0.7rem;
    background: var(--panel2); border: 2px solid var(--border); height: 16px;
    position: relative; overflow: hidden;
  }
  .xp-bar-fill {
    height: 100%; background: linear-gradient(90deg, var(--green), #6fcf52);
    transition: width 1s ease;
    position: relative;
  }
  .xp-bar-fill::after {
    content: ''; position: absolute; inset: 0;
    background: repeating-linear-gradient(90deg, transparent 0 8px, rgba(255,255,255,0.2) 8px 10px);
  }
  .xp-label {
    font-family: 'Press Start 2P', monospace; font-size: 0.45rem;
    color: var(--wood2); margin-top: 2px;
  }

  /* ── FLOATING ITEMS ── */
  .float-item {
    position: fixed; z-index: 10;
    font-size: 1.5rem;
    animation: floatUp 3s ease-out forwards;
    pointer-events: none;
  }
  @keyframes floatUp {
    0%   { opacity: 1; transform: translateY(0); }
    100% { opacity: 0; transform: translateY(-80px); }
  }

  /* ── PIXEL DIVIDER ── */
  .px-divider {
    height: 8px; margin: 0.2rem 0;
    background: repeating-linear-gradient(90deg, var(--border) 0 4px, transparent 4px 8px);
    opacity: 0.3;
  }

  /* ── SCROLL TOP BTN ── */
  #scrollTop {
    position: fixed; bottom: 70px; right: 20px; z-index: 50;
    background: var(--wood); border: 3px solid var(--border);
    color: var(--gold); font-family: 'Press Start 2P', monospace; font-size: 0.6rem;
    padding: 0.5rem 0.7rem; cursor: pointer;
    box-shadow: 3px 3px 0 var(--shadow);
    display: none;
    transition: transform 0.15s;
  }
  #scrollTop:hover { transform: translate(-2px, -2px); box-shadow: 5px 5px 0 var(--shadow); }
  #scrollTop.visible { display: block; }

  /* delay helpers */
  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.3s; }
  .delay-4 { animation-delay: 0.4s; }
  .delay-5 { animation-delay: 0.5s; }

  @media (max-width: 500px) {
    .nameplate-inner { flex-direction: column; }
    .page { padding: 1rem 0.75rem 6rem; }
  }
</style>
</head>
<body>

<!-- SKY + ENVIRONMENT -->
<div class="sky-bg"></div>
<div class="cloud"></div>
<div class="cloud"></div>
<div class="cloud"></div>
<div class="ground"></div>

<!-- TOAST -->
<div id="toast">✨ New achievement unlocked!</div>

<!-- SCROLL TOP -->
<button id="scrollTop" onclick="window.scrollTo({top:0,behavior:'smooth'})">▲ TOP</button>

<div class="page">

  <!-- ══════ NAMEPLATE ══════ -->
  <div class="nameplate">
    <div class="nameplate-inner">
      <!-- Pixel sprite drawn via canvas -->
      <div class="sprite">
        <canvas id="playerCanvas" width="64" height="80"></canvas>
      </div>
      <div class="name-block">
        <h1>SAMANTHA<br/>SOLOMON</h1>
        <div class="job-title">⚔ Campaign Manager</div>
        <div class="contact-row">
          <span>📍 Dallas, TX</span>
          <span>·</span>
          <a href="tel:2146326082">📞 (214) 632-6082</a>
          <span>·</span>
          <a href="mailto:samisolomon31@gmail.com">✉ samisolomon31@gmail.com</a>
        </div>
        <div class="stars-row">
          <span class="star">★</span><span class="star">★</span><span class="star">★</span><span class="star">★</span><span class="star">★</span>
          <span style="font-size:1rem; color:var(--wood); margin-left:6px;">Friendship Level MAX</span>
        </div>
        <!-- XP bar -->
        <div class="xp-label">Campaign XP ████████████ LVL 99</div>
        <div class="xp-bar-wrap"><div class="xp-bar-fill" style="width:94%"></div></div>
      </div>
    </div>
  </div>

  <!-- ══════ SUMMARY ══════ -->
  <div class="panel delay-1">
    <div class="panel-header" onclick="togglePanel(this)">
      <span class="panel-icon">📖</span>
      <h2>PLAYER BIO</h2>
      <button class="toggle-btn open">▼</button>
    </div>
    <div class="panel-body" style="max-height:300px">
      <div class="summary-text">
        Results-driven Campaign Manager seeking her next quest. Equipped with a degree in Strategic Communications and minors in Marketing &amp; Business Analytics. Blessed with unwavering attention to detail, a deep passion for data, and an outgoing personality that levels up any party she joins.
      </div>
    </div>
  </div>

  <!-- ══════ EXPERIENCE ══════ -->
  <div class="panel delay-2">
    <div class="panel-header" onclick="togglePanel(this)">
      <span class="panel-icon">⚔️</span>
      <h2>QUEST LOG</h2>
      <button class="toggle-btn open">▼</button>
    </div>
    <div class="panel-body" style="max-height:2000px">

      <!-- Job 1 -->
      <div class="job-card" onclick="toggleJob(this)">
        <div class="job-header">
          <div>
            <div class="job-title-text">CAMPAIGN MGR — TECHNOLOGY</div>
            <div class="job-company">🏰 RAPP Dallas</div>
          </div>
          <div>
            <div class="job-date">📅 Nov 2024 – Present</div>
            <div style="font-size:0.85rem; color:var(--green); text-align:right;">▶ Active Quest</div>
          </div>
        </div>
        <div class="job-body" style="max-height:600px">
          <div class="job-bullet">Own campaign implementation, management &amp; monitoring on Salesforce Marketing Cloud, Adobe Experience Platform, Pega, and Braze</div>
          <div class="job-bullet">Create segments using SQL; design complex multi-channel journeys with dynamic content and trigger-based deployment</div>
          <div class="job-bullet">Monitor deployments &amp; deliverability; troubleshoot and resolve issues in a timely manner</div>
          <div class="job-bullet">Partner with Marketing Sciences team to set up and track campaigns</div>
          <div class="job-bullet">Analyze campaign performance and drive data-backed client decisions</div>
          <div class="job-bullet">Pivot as needed for ad-hoc data, campaign planning, and execution requests</div>
        </div>
      </div>

      <!-- Job 2 -->
      <div class="job-card" onclick="toggleJob(this)">
        <div class="job-header">
          <div>
            <div class="job-title-text">CAMPAIGN MGR — PRODUCTION &amp; EXECUTION</div>
            <div class="job-company">🌾 Mesmerize</div>
          </div>
          <div>
            <div class="job-date">📅 Jan 2024 – Oct 2024</div>
            <div style="font-size:0.85rem; color:var(--gold2); text-align:right;">✔ Completed</div>
          </div>
        </div>
        <div class="job-body" style="max-height:600px">
          <div class="job-bullet">Oversaw campaign execution start-to-finish: accuracy in sales orders, Trello status tracking, and kick-off call scheduling</div>
          <div class="job-bullet">Communicated campaign details, ordered &amp; produced materials, coordinated shipping, and verified location specs for on-time launches</div>
          <div class="job-bullet">Acted as primary internal contact for all campaign development and execution knowledge</div>
          <div class="job-bullet">Managed campaign budgets to ensure profitability and cost efficiency</div>
          <div class="job-bullet">Conducted research for strategic insight, achieving above-target outcomes through cross-functional communication</div>
        </div>
      </div>

      <!-- Job 3 -->
      <div class="job-card" onclick="toggleJob(this)">
        <div class="job-header">
          <div>
            <div class="job-title-text">CAMPAIGN MGR — CSR OPERATIONS</div>
            <div class="job-company">🌾 Mesmerize</div>
          </div>
          <div>
            <div class="job-date">📅 Apr 2023 – Jan 2024</div>
            <div style="font-size:0.85rem; color:var(--gold2); text-align:right;">✔ Completed</div>
          </div>
        </div>
        <div class="job-body" style="max-height:600px">
          <div class="job-bullet">Developed campaign execution plans and problem-solved issues as they arose</div>
          <div class="job-bullet">Developed, monitored, and tracked KPIs to keep priorities on track</div>
          <div class="job-bullet">Oversaw call service representatives through communication, coaching, and KPI tracking</div>
          <div class="job-bullet">Ongoing data analysis of business operations; made data-driven decisions to drive multiple campaigns simultaneously</div>
        </div>
      </div>

    </div>
  </div>

  <!-- ══════ SKILLS ══════ -->
  <div class="panel delay-3">
    <div class="panel-header" onclick="togglePanel(this)">
      <span class="panel-icon">🛠️</span>
      <h2>SKILL TREE</h2>
      <button class="toggle-btn open">▼</button>
    </div>
    <div class="panel-body" style="max-height:800px">
      <div class="skills-grid">
        <div class="skill-item" onclick="spawnItem(this,'⚡')">Salesforce Lightning &amp; Marketing Cloud</div>
        <div class="skill-item" onclick="spawnItem(this,'📊')">SQL — Segmentation &amp; Querying</div>
        <div class="skill-item" onclick="spawnItem(this,'🔗')">Adobe Experience Platform</div>
        <div class="skill-item" onclick="spawnItem(this,'📱')">Pega &amp; Braze</div>
        <div class="skill-item" onclick="spawnItem(this,'📋')">Workfront &amp; Trello</div>
        <div class="skill-item" onclick="spawnItem(this,'💬')">Cross-Functional Communication</div>
        <div class="skill-item" onclick="spawnItem(this,'🔍')">KPI Development &amp; Tracking</div>
        <div class="skill-item" onclick="spawnItem(this,'💡')">Proactive Problem Solving</div>
        <div class="skill-item" onclick="spawnItem(this,'📈')">Campaign Performance Analysis</div>
        <div class="skill-item" onclick="spawnItem(this,'📎')">Microsoft Excel, PowerPoint &amp; Word</div>
        <div class="skill-item" onclick="spawnItem(this,'🎯')">Budget Management</div>
        <div class="skill-item" onclick="spawnItem(this,'🤝')">Stakeholder Communication</div>
      </div>
    </div>
  </div>

  <!-- ══════ CERTIFICATIONS ══════ -->
  <div class="panel delay-4">
    <div class="panel-header" onclick="togglePanel(this)">
      <span class="panel-icon">🏆</span>
      <h2>ACHIEVEMENTS</h2>
      <button class="toggle-btn open">▼</button>
    </div>
    <div class="panel-body" style="max-height:600px">
      <div class="cert-list">
        <div class="cert-item" onclick="spawnItem(this,'🏆')">
          <span class="cert-badge">📊</span> Microsoft Excel, PowerPoint &amp; Word Certified
          <span class="cert-year">2021</span>
        </div>
        <div class="cert-item" onclick="spawnItem(this,'🏆')">
          <span class="cert-badge">🗄️</span> Microsoft Access Certified
          <span class="cert-year">2022</span>
        </div>
        <div class="cert-item" onclick="spawnItem(this,'🏆')">
          <span class="cert-badge">🥋</span> Six Sigma Yellow Belt
          <span class="cert-year">2023</span>
        </div>
        <div class="cert-item" onclick="spawnItem(this,'🌟')">
          <span class="cert-badge">🥇</span> Six Sigma Green Belt
          <span class="cert-year">2024</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ══════ EDUCATION ══════ -->
  <div class="panel delay-5">
    <div class="panel-header" onclick="togglePanel(this)">
      <span class="panel-icon">🎓</span>
      <h2>ORIGIN STORY</h2>
      <button class="toggle-btn open">▼</button>
    </div>
    <div class="panel-body" style="max-height:300px">
      <div class="edu-card">
        <div class="edu-icon">🏛️</div>
        <div>
          <div class="edu-name">UNIVERSITY OF DENVER</div>
          <div class="edu-degree">Bachelor's Degree — Strategic Communications</div>
          <div>Minors: Marketing &amp; Business Analytics</div>
          <div class="edu-years">📅 2018 – 2023</div>
        </div>
      </div>
    </div>
  </div>

</div><!-- /page -->

<script>
  // ── PANEL TOGGLE ──
  function togglePanel(header) {
    const body = header.nextElementSibling;
    const btn  = header.querySelector('.toggle-btn');
    body.classList.toggle('collapsed');
    btn.classList.toggle('open');
  }

  // ── JOB TOGGLE ──
  function toggleJob(card) {
    const body = card.querySelector('.job-body');
    body.classList.toggle('collapsed');
    showToast(body.classList.contains('collapsed') ? '📜 Quest details hidden' : '📜 Quest details revealed!');
  }

  // ── TOAST ──
  let toastTimer;
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => t.classList.remove('show'), 2200);
  }

  // ── FLOATING ITEM ON CLICK ──
  function spawnItem(el, emoji) {
    const rect = el.getBoundingClientRect();
    const div = document.createElement('div');
    div.className = 'float-item';
    div.textContent = emoji;
    div.style.left = (rect.left + rect.width/2 - 12) + 'px';
    div.style.top  = (rect.top  + window.scrollY - 10) + 'px';
    document.body.appendChild(div);
    setTimeout(() => div.remove(), 3100);
    showToast('✨ Skill activated!');
  }

  // ── SCROLL TOP ──
  window.addEventListener('scroll', () => {
    document.getElementById('scrollTop').classList.toggle('visible', window.scrollY > 300);
  });

  // ── PIXEL CHARACTER CANVAS ──
  const c = document.getElementById('playerCanvas');
  const ctx = c.getContext('2d');
  ctx.imageSmoothingEnabled = false;

  // Simple pixel-art character (each cell = 4px)
  const S = 4;
  function px(x, y, color) {
    ctx.fillStyle = color;
    ctx.fillRect(x * S, y * S, S, S);
  }

  function drawCharacter(frame) {
    ctx.clearRect(0, 0, 64, 80);
    // Hair
    [[3,1],[4,1],[5,1],[6,1],[3,2],[6,2],[2,2],[7,2]].forEach(([x,y]) => px(x,y,'#c0392b'));
    // Face
    [[3,2],[4,2],[5,2],[6,2],[3,3],[4,3],[5,3],[6,3],[3,4],[4,4],[5,4],[6,4]].forEach(([x,y]) => px(x,y,'#f5cba7'));
    // Eyes
    px(4,3,'#5d4037'); px(5,3,'#5d4037');
    // Smile
    px(4,4,'#e74c3c'); px(5,4,'#e74c3c');
    // Body (blue shirt)
    [[2,5],[3,5],[4,5],[5,5],[6,5],[7,5],[2,6],[3,6],[4,6],[5,6],[6,6],[7,6],
     [2,7],[3,7],[4,7],[5,7],[6,7],[7,7]].forEach(([x,y]) => px(x,y,'#2980b9'));
    // Pants
    [[2,8],[3,8],[4,8],[5,8],[6,8],[7,8],[2,9],[3,9],[4,9],[5,9],[6,9],[7,9]].forEach(([x,y]) => px(x,y,'#5d4037'));
    // Shoes
    [[2,10],[3,10],[4,10]].forEach(([x,y]) => px(x,y,'#2c1a0e'));
    [[5,10],[6,10],[7,10]].forEach(([x,y]) => px(x,y,'#2c1a0e'));
    // Arms (animated)
    const armY = frame === 0 ? 6 : 5;
    px(1, armY, '#2980b9'); px(8, armY, '#2980b9');
    // Briefcase
    px(8, 7, '#f0c040'); px(9, 7, '#f0c040'); px(8, 8, '#f0c040'); px(9, 8, '#f0c040');
    px(8, 6, '#d4a017'); px(9, 6, '#d4a017');
  }

  let frame = 0;
  setInterval(() => { frame = 1 - frame; drawCharacter(frame); }, 700);
  drawCharacter(0);

  // ── EASTER EGG: Konami code ──
  let keys = [];
  const konami = ['ArrowUp','ArrowUp','ArrowDown','ArrowDown','ArrowLeft','ArrowRight','ArrowLeft','ArrowRight','b','a'];
  document.addEventListener('keydown', e => {
    keys.push(e.key);
    keys = keys.slice(-10);
    if (keys.join(',') === konami.join(',')) {
      showToast('🌟 SECRET FOUND! You unlocked: Hired!');
      for (let i = 0; i < 12; i++) {
        setTimeout(() => {
          const div = document.createElement('div');
          div.className = 'float-item';
          div.textContent = ['🌟','💛','🏆','⭐','✨'][Math.floor(Math.random()*5)];
          div.style.left = Math.random() * (window.innerWidth - 40) + 'px';
          div.style.top = (Math.random() * window.innerHeight + window.scrollY) + 'px';
          document.body.appendChild(div);
          setTimeout(() => div.remove(), 3100);
        }, i * 120);
      }
    }
  });

  // ── Initial greeting ──
  setTimeout(() => showToast('👋 Welcome to Samantha\'s farm! Click anything!'), 1000);
</script>
</body>
</html>
