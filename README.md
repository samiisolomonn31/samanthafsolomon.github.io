<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>GitHub — Where Code Lives</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg:        #0d1b3e;
      --bg2:       #0a1628;
      --surface:   #112357;
      --accent:    #4f8ef7;
      --accent2:   #a0c4ff;
      --glow:      #4f8ef780;
      --white:     #e8f0ff;
      --muted:     #7a9cc4;
      --border:    #1e3a6e;
      --card:      #0f1f4a;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'JetBrains Mono', monospace;
      background: var(--bg);
      color: var(--white);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── BACKGROUND MESH ── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background:
        radial-gradient(ellipse 80% 60% at 20% 10%, #1a3a8a55 0%, transparent 60%),
        radial-gradient(ellipse 60% 50% at 80% 80%, #0a2a6055 0%, transparent 60%),
        radial-gradient(ellipse 40% 40% at 60% 30%, #4f8ef720 0%, transparent 50%);
      pointer-events: none;
      z-index: 0;
    }

    /* ── GRID OVERLAY ── */
    body::after {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(var(--border) 1px, transparent 1px),
        linear-gradient(90deg, var(--border) 1px, transparent 1px);
      background-size: 60px 60px;
      opacity: 0.25;
      pointer-events: none;
      z-index: 0;
    }

    /* ── NAV ── */
    nav {
      position: sticky; top: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1rem 3rem;
      background: #0a1628cc;
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }

    .logo {
      display: flex; align-items: center; gap: 0.7rem;
      font-family: 'Syne', sans-serif;
      font-weight: 800; font-size: 1.25rem;
      letter-spacing: -0.03em;
      color: var(--white);
      text-decoration: none;
    }

    .logo svg { width: 30px; height: 30px; fill: var(--accent); }

    nav ul {
      display: flex; gap: 2rem; list-style: none;
    }
    nav ul a {
      color: var(--muted); text-decoration: none; font-size: 0.85rem;
      transition: color 0.2s;
    }
    nav ul a:hover { color: var(--accent2); }

    .nav-cta {
      background: var(--accent);
      color: #fff !important;
      padding: 0.5rem 1.2rem;
      border-radius: 6px;
      font-weight: 500;
      transition: box-shadow 0.2s, background 0.2s !important;
    }
    .nav-cta:hover {
      background: #6aa0ff !important;
      box-shadow: 0 0 20px var(--glow);
      color: #fff !important;
    }

    /* ── HERO ── */
    .hero {
      position: relative; z-index: 1;
      display: flex; flex-direction: column; align-items: center;
      text-align: center;
      padding: 7rem 2rem 5rem;
    }

    .hero-badge {
      display: inline-flex; align-items: center; gap: 0.5rem;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 100px;
      padding: 0.35rem 1rem;
      font-size: 0.75rem;
      color: var(--accent2);
      margin-bottom: 2rem;
      animation: fadeUp 0.6s ease both;
    }
    .hero-badge span { width: 6px; height: 6px; background: #4ade80; border-radius: 50%; animation: pulse 2s infinite; }

    @keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.3;} }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2.8rem, 7vw, 5.5rem);
      font-weight: 800;
      line-height: 1.05;
      letter-spacing: -0.04em;
      max-width: 800px;
      animation: fadeUp 0.7s ease 0.1s both;
    }

    h1 .highlight {
      background: linear-gradient(120deg, var(--accent), var(--accent2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-sub {
      margin-top: 1.5rem;
      font-size: clamp(0.95rem, 2vw, 1.1rem);
      color: var(--muted);
      max-width: 560px;
      line-height: 1.7;
      animation: fadeUp 0.7s ease 0.2s both;
    }

    .hero-actions {
      display: flex; gap: 1rem; margin-top: 2.5rem; flex-wrap: wrap; justify-content: center;
      animation: fadeUp 0.7s ease 0.3s both;
    }

    .btn-primary {
      background: var(--accent);
      color: #fff;
      padding: 0.85rem 2rem;
      border-radius: 8px;
      border: none; cursor: pointer;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.9rem;
      font-weight: 500;
      text-decoration: none;
      transition: box-shadow 0.25s, transform 0.25s;
    }
    .btn-primary:hover {
      box-shadow: 0 0 30px var(--glow);
      transform: translateY(-2px);
    }

    .btn-ghost {
      background: transparent;
      color: var(--white);
      padding: 0.85rem 2rem;
      border-radius: 8px;
      border: 1px solid var(--border);
      cursor: pointer;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.9rem;
      text-decoration: none;
      transition: border-color 0.25s, color 0.25s, transform 0.25s;
    }
    .btn-ghost:hover {
      border-color: var(--accent);
      color: var(--accent2);
      transform: translateY(-2px);
    }

    /* ── STATS ── */
    .stats {
      position: relative; z-index: 1;
      display: flex; justify-content: center; gap: 4rem; flex-wrap: wrap;
      padding: 3rem 2rem;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      animation: fadeUp 0.7s ease 0.4s both;
    }
    .stat h3 {
      font-family: 'Syne', sans-serif;
      font-size: 2.2rem; font-weight: 800;
      color: var(--accent2);
      letter-spacing: -0.04em;
    }
    .stat p { color: var(--muted); font-size: 0.8rem; margin-top: 0.2rem; }

    /* ── TERMINAL CARD ── */
    .terminal-wrap {
      position: relative; z-index: 1;
      display: flex; justify-content: center;
      padding: 4rem 2rem;
      animation: fadeUp 0.7s ease 0.45s both;
    }

    .terminal {
      background: #060f28;
      border: 1px solid var(--border);
      border-radius: 12px;
      width: 100%; max-width: 680px;
      overflow: hidden;
      box-shadow: 0 0 60px #0a1628cc, 0 0 100px #4f8ef720;
    }

    .terminal-bar {
      background: #0d1b3e;
      padding: 0.8rem 1rem;
      display: flex; align-items: center; gap: 0.5rem;
      border-bottom: 1px solid var(--border);
    }
    .dot { width: 12px; height: 12px; border-radius: 50%; }
    .dot.r { background: #ff5f57; }
    .dot.y { background: #ffbd2e; }
    .dot.g { background: #28c840; }
    .terminal-title { margin-left: 0.5rem; color: var(--muted); font-size: 0.78rem; }

    .terminal-body { padding: 1.5rem 1.8rem; font-size: 0.85rem; line-height: 1.9; }
    .term-comment { color: #3d5a8a; }
    .term-cmd { color: var(--accent2); }
    .term-out { color: #7a9cc4; }
    .term-success { color: #4ade80; }
    .term-file { color: #f59e0b; }
    .cursor {
      display: inline-block; width: 9px; height: 1em;
      background: var(--accent); margin-left: 2px; vertical-align: text-bottom;
      animation: blink 1s step-end infinite;
    }
    @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0;} }

    /* ── FEATURE CARDS ── */
    .features {
      position: relative; z-index: 1;
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem; padding: 2rem 3rem 5rem;
      max-width: 1200px; margin: 0 auto;
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 2rem;
      transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
      animation: fadeUp 0.6s ease both;
    }
    .card:hover {
      border-color: var(--accent);
      transform: translateY(-4px);
      box-shadow: 0 12px 40px #0a162880, 0 0 20px var(--glow);
    }

    .card-icon {
      width: 44px; height: 44px;
      background: var(--surface);
      border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.3rem; margin-bottom: 1.2rem;
    }

    .card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1.05rem; font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .card p { color: var(--muted); font-size: 0.8rem; line-height: 1.7; }

    /* ── FOOTER ── */
    footer {
      position: relative; z-index: 1;
      text-align: center;
      padding: 2rem;
      border-top: 1px solid var(--border);
      color: var(--muted);
      font-size: 0.78rem;
    }
    footer a { color: var(--accent2); text-decoration: none; }

    /* ── SECTION LABEL ── */
    .section-label {
      position: relative; z-index: 1;
      text-align: center;
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--accent);
      padding-top: 4rem;
      animation: fadeUp 0.6s ease 0.5s both;
    }
    .section-title {
      position: relative; z-index: 1;
      text-align: center;
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.6rem, 4vw, 2.5rem);
      font-weight: 800;
      letter-spacing: -0.03em;
      margin-top: 0.5rem; margin-bottom: 2.5rem;
      animation: fadeUp 0.6s ease 0.55s both;
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a class="logo" href="#">
      <svg viewBox="0 0 98 96" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z"/>
      </svg>
      Samantha Solomon
    </a>
    <ul>
      <li><a href="#">Product</a></li>
      <li><a href="#">Solutions</a></li>
      <li><a href="#">Docs</a></li>
      <li><a href="#">Pricing</a></li>
      <li><a href="#" class="nav-cta">Sign up</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-badge"><span></span> 100M+ developers worldwide</div>
    <h1>Build the future,<br/><span class="highlight">one commit</span> at a time.</h1>
    <p class="hero-sub">
      The world's leading platform for version control, collaboration, and open-source software — reimagined with a blue horizon.
    </p>
    <div class="hero-actions">
      <a class="btn-primary" href="#">Start for free</a>
      <a class="btn-ghost" href="#">Explore repositories →</a>
    </div>
  </section>

  <!-- STATS -->
  <div class="stats">
    <div class="stat"><h3>100M+</h3><p>Developers</p></div>
    <div class="stat"><h3>372M+</h3><p>Repositories</p></div>
    <div class="stat"><h3>4M+</h3><p>Organizations</p></div>
    <div class="stat"><h3>90%</h3><p>Fortune 100 companies</p></div>
  </div>

  <!-- TERMINAL -->
  <div class="terminal-wrap">
    <div class="terminal">
      <div class="terminal-bar">
        <div class="dot r"></div>
        <div class="dot y"></div>
        <div class="dot g"></div>
        <span class="terminal-title">bash — ~/my-project</span>
      </div>
      <div class="terminal-body">
        <div class="term-comment"># Clone your project in seconds</div>
        <div><span class="term-cmd">$</span> git clone https://github.com/you/awesome-project</div>
        <div class="term-out">Cloning into 'awesome-project'...</div>
        <div class="term-out">remote: Enumerating objects: 1,042 done.</div>
        <div class="term-success">✔ Done. 1042 objects received.</div>
        <br/>
        <div><span class="term-cmd">$</span> git checkout -b <span class="term-file">feature/blue-ui</span></div>
        <div class="term-success">✔ Switched to new branch 'feature/blue-ui'</div>
        <br/>
        <div><span class="term-cmd">$</span> git push origin feature/blue-ui<span class="cursor"></span></div>
      </div>
    </div>
  </div>

  <!-- FEATURES -->
  <p class="section-label">Why GitBlue</p>
  <h2 class="section-title">Everything your team needs</h2>

  <div class="features">
    <div class="card" style="animation-delay:0.1s">
      <div class="card-icon">🔀</div>
      <h3>Pull Requests</h3>
      <p>Collaborate on code changes with built-in review tools, inline comments, and automated status checks.</p>
    </div>
    <div class="card" style="animation-delay:0.2s">
      <div class="card-icon">⚡</div>
      <h3>GitHub Actions</h3>
      <p>Automate your CI/CD pipeline directly in your repository. Build, test, and deploy on every push.</p>
    </div>
    <div class="card" style="animation-delay:0.3s">
      <div class="card-icon">🛡️</div>
      <h3>Security Scanning</h3>
      <p>Automatically detect vulnerabilities in your dependencies and get actionable remediation advice.</p>
    </div>
    <div class="card" style="animation-delay:0.4s">
      <div class="card-icon">📦</div>
      <h3>Packages</h3>
      <p>Host and manage your packages alongside your code — npm, Docker, Maven, and more in one place.</p>
    </div>
    <div class="card" style="animation-delay:0.5s">
      <div class="card-icon">🗂️</div>
      <h3>Projects</h3>
      <p>Plan and track your work with flexible Kanban boards, roadmaps, and issue tracking built in.</p>
    </div>
    <div class="card" style="animation-delay:0.6s">
      <div class="card-icon">🌐</div>
      <h3>GitHub Pages</h3>
      <p>Deploy your websites directly from a repository. Free hosting with custom domain support included.</p>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <p>© 2026 Samantha Solomon, Inc. · <a href="#">Privacy</a> · <a href="#">Terms</a> · <a href="#">Status</a></p>
  </footer>

</body>
</html>
