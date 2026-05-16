<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Resume — Product &amp; Platform Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;600;700;800&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet" />
<style>
  /* ============================================================
     THEME TOKENS
     ============================================================ */
  :root {
    --bg-0:        #05070d;
    --bg-1:        #0a0e1a;
    --panel:       rgba(18, 24, 41, 0.55);
    --panel-edge:  rgba(120, 160, 255, 0.16);
    --ink:         #e8ecf6;
    --ink-soft:    #9aa6c4;
    --ink-faint:   #5d6a8c;
    --cyan:        #38e8ff;
    --violet:      #8b7dff;
    --lime:        #8effc1;
    --amber:       #ffd166;
    --grid:        rgba(120, 160, 255, 0.06);
    --glow-cyan:   rgba(56, 232, 255, 0.35);
    --glow-violet: rgba(139, 125, 255, 0.30);
    --r:           18px;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg-0);
    color: var(--ink);
    font-family: 'Sora', sans-serif;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
    overflow-x: hidden;
  }

  /* ============================================================
     ANIMATED BACKGROUND
     ============================================================ */
  .bg-layer {
    position: fixed;
    inset: 0;
    z-index: -2;
    background:
      radial-gradient(800px 500px at 12% 8%, rgba(56,232,255,0.10), transparent 60%),
      radial-gradient(700px 600px at 88% 90%, rgba(139,125,255,0.12), transparent 60%),
      linear-gradient(180deg, var(--bg-0), var(--bg-1));
  }
  .bg-grid {
    position: fixed;
    inset: 0;
    z-index: -1;
    background-image:
      linear-gradient(var(--grid) 1px, transparent 1px),
      linear-gradient(90deg, var(--grid) 1px, transparent 1px);
    background-size: 56px 56px;
    mask-image: radial-gradient(ellipse 90% 70% at 50% 40%, #000 35%, transparent 100%);
    animation: drift 40s linear infinite;
  }
  @keyframes drift {
    from { background-position: 0 0, 0 0; }
    to   { background-position: 56px 56px, 56px 56px; }
  }
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    z-index: -1;
    opacity: 0.5;
    pointer-events: none;
  }
  .orb-a { width: 380px; height: 380px; background: var(--glow-cyan);   top: -120px; left: -100px; animation: float1 18s ease-in-out infinite; }
  .orb-b { width: 420px; height: 420px; background: var(--glow-violet); bottom: -160px; right: -120px; animation: float2 22s ease-in-out infinite; }
  @keyframes float1 { 50% { transform: translate(60px, 50px); } }
  @keyframes float2 { 50% { transform: translate(-50px, -40px); } }

  /* ============================================================
     LAYOUT
     ============================================================ */
  .wrap {
    max-width: 1080px;
    margin: 0 auto;
    padding: 56px 28px 80px;
  }

  /* ---- HERO ---- */
  .hero {
    position: relative;
    border: 1px solid var(--panel-edge);
    border-radius: var(--r);
    background: var(--panel);
    backdrop-filter: blur(14px);
    -webkit-backdrop-filter: blur(14px);
    padding: 40px 40px 36px;
    overflow: hidden;
  }
  .hero::before {
    content: "";
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--cyan), var(--violet), transparent);
  }
  .scanline {
    position: absolute;
    left: 0; right: 0;
    height: 120px;
    background: linear-gradient(180deg, transparent, rgba(56,232,255,0.06), transparent);
    pointer-events: none;
    animation: scan 7s linear infinite;
  }
  @keyframes scan {
    0%   { top: -120px; }
    100% { top: 100%; }
  }

  .hero-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 18px;
  }
  .status {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--lime);
    border: 1px solid rgba(142,255,193,0.25);
    background: rgba(142,255,193,0.06);
    padding: 6px 12px;
    border-radius: 100px;
  }
  .dot {
    width: 7px; height: 7px; border-radius: 50%;
    background: var(--lime);
    box-shadow: 0 0 10px var(--lime);
    animation: pulse 1.8s ease-in-out infinite;
  }
  @keyframes pulse { 50% { opacity: 0.3; transform: scale(0.7); } }

  .clock {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--ink-faint);
    letter-spacing: 0.06em;
  }

  .name {
    margin-top: 26px;
    font-size: clamp(2.6rem, 6vw, 4.2rem);
    font-weight: 800;
    line-height: 1.02;
    letter-spacing: -0.02em;
    background: linear-gradient(120deg, #ffffff 20%, var(--cyan) 60%, var(--violet) 100%);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }
  .role-line {
    margin-top: 10px;
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(0.9rem, 2vw, 1.05rem);
    color: var(--cyan);
    letter-spacing: 0.04em;
  }
  .role-line .cursor {
    display: inline-block;
    width: 9px; height: 1.05em;
    background: var(--cyan);
    margin-left: 2px;
    vertical-align: -2px;
    animation: blink 1s steps(1) infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  .summary {
    margin-top: 20px;
    max-width: 640px;
    color: var(--ink-soft);
    font-size: 0.98rem;
  }

  .contact {
    margin-top: 26px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .chip {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--ink-soft);
    border: 1px solid var(--panel-edge);
    background: rgba(255,255,255,0.02);
    padding: 8px 13px;
    border-radius: 10px;
    text-decoration: none;
    transition: all 0.25s ease;
  }
  .chip:hover {
    color: var(--ink);
    border-color: var(--cyan);
    box-shadow: 0 0 18px rgba(56,232,255,0.15);
    transform: translateY(-2px);
  }
  .chip svg { width: 14px; height: 14px; }

  /* ---- SECTION HEADERS ---- */
  .section { margin-top: 46px; }
  .sec-head {
    display: flex;
    align-items: baseline;
    gap: 14px;
    margin-bottom: 22px;
  }
  .sec-idx {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--cyan);
    opacity: 0.8;
  }
  .sec-title {
    font-size: 1.35rem;
    font-weight: 700;
    letter-spacing: -0.01em;
  }
  .sec-rule {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--panel-edge), transparent);
  }

  /* ---- CARDS / PANELS ---- */
  .panel {
    border: 1px solid var(--panel-edge);
    border-radius: var(--r);
    background: var(--panel);
    backdrop-filter: blur(14px);
    -webkit-backdrop-filter: blur(14px);
    padding: 26px 28px;
    position: relative;
    transition: border-color 0.3s ease, transform 0.3s ease;
  }
  .panel:hover {
    border-color: rgba(120,160,255,0.34);
    transform: translateY(-3px);
  }

  /* ---- TIMELINE / EXPERIENCE ---- */
  .timeline { display: flex; flex-direction: column; gap: 18px; }
  .job {
    display: grid;
    grid-template-columns: 150px 1fr;
    gap: 24px;
  }
  .job-when {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--ink-faint);
    padding-top: 4px;
  }
  .job-when .now {
    color: var(--lime);
    display: block;
    margin-top: 4px;
  }
  .job-role {
    font-size: 1.1rem;
    font-weight: 600;
  }
  .job-org {
    color: var(--cyan);
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    margin-top: 2px;
  }
  .job-points {
    margin-top: 12px;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 7px;
  }
  .job-points li {
    position: relative;
    padding-left: 20px;
    color: var(--ink-soft);
    font-size: 0.93rem;
  }
  .job-points li::before {
    content: "▹";
    position: absolute;
    left: 0;
    color: var(--violet);
  }

  /* ---- SKILLS ---- */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 16px;
  }
  .skill-cat {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    color: var(--amber);
    margin-bottom: 14px;
  }
  .skill-row { margin-bottom: 14px; }
  .skill-row:last-child { margin-bottom: 0; }
  .skill-name {
    display: flex;
    justify-content: space-between;
    font-size: 0.85rem;
    margin-bottom: 6px;
  }
  .skill-name span:last-child {
    font-family: 'JetBrains Mono', monospace;
    color: var(--ink-faint);
    font-size: 11px;
  }
  .bar {
    height: 6px;
    background: rgba(255,255,255,0.05);
    border-radius: 100px;
    overflow: hidden;
  }
  .bar-fill {
    height: 100%;
    border-radius: 100px;
    width: 0;
    background: linear-gradient(90deg, var(--cyan), var(--violet));
    transition: width 1.4s cubic-bezier(0.16, 1, 0.3, 1);
  }

  /* ---- METRICS ---- */
  .metrics {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 16px;
  }
  .metric {
    text-align: center;
    padding: 22px 14px;
  }
  .metric-num {
    font-size: 2.4rem;
    font-weight: 800;
    font-family: 'Sora', sans-serif;
    background: linear-gradient(120deg, var(--cyan), var(--lime));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    line-height: 1;
  }
  .metric-label {
    margin-top: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--ink-faint);
  }

  /* ---- TAGS ---- */
  .tags { display: flex; flex-wrap: wrap; gap: 9px; }
  .tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--ink-soft);
    border: 1px solid var(--panel-edge);
    background: rgba(255,255,255,0.02);
    padding: 6px 12px;
    border-radius: 8px;
    transition: all 0.2s ease;
  }
  .tag:hover {
    color: var(--bg-0);
    background: var(--cyan);
    border-color: var(--cyan);
  }

  /* ---- TWO COLUMN ---- */
  .two-col {
    display: grid;
    grid-template-columns: 1.4fr 1fr;
    gap: 18px;
  }

  .edu-item { margin-bottom: 18px; }
  .edu-item:last-child { margin-bottom: 0; }
  .edu-deg { font-weight: 600; font-size: 1rem; }
  .edu-school {
    color: var(--cyan);
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    margin-top: 2px;
  }
  .edu-meta {
    color: var(--ink-faint);
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    margin-top: 4px;
  }

  /* ---- FOOTER ---- */
  .footer {
    margin-top: 56px;
    text-align: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--ink-faint);
    letter-spacing: 0.08em;
  }
  .footer .dot-sm {
    color: var(--violet);
    margin: 0 8px;
  }

  /* ---- REVEAL ANIMATION ---- */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.7s ease, transform 0.7s cubic-bezier(0.16,1,0.3,1);
  }
  .reveal.in { opacity: 1; transform: none; }

  /* ---- PRINT ---- */
  @media print {
    .bg-layer, .bg-grid, .orb, .scanline, .clock { display: none !important; }
    body { background: #fff; color: #111; }
    .wrap { padding: 0; }
    .panel, .hero { background: #fff; border-color: #ccc; box-shadow: none; backdrop-filter: none; }
    .reveal { opacity: 1 !important; transform: none !important; }
    .name, .metric-num { -webkit-text-fill-color: #111; color: #111; }
    .bar-fill { background: #444 !important; }
    .section { page-break-inside: avoid; }
  }

  /* ---- RESPONSIVE ---- */
  @media (max-width: 680px) {
    .wrap { padding: 32px 16px 60px; }
    .hero { padding: 28px 22px; }
    .job { grid-template-columns: 1fr; gap: 6px; }
    .two-col { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="bg-layer"></div>
<div class="bg-grid"></div>
<div class="orb orb-a"></div>
<div class="orb orb-b"></div>

<div class="wrap">

  <!-- ================= HERO ================= -->
  <header class="hero reveal">
    <div class="scanline"></div>
    <div class="hero-top">
      <span class="status"><span class="dot"></span> Available for opportunities</span>
      <span class="clock" id="clock">--:--:-- UTC</span>
    </div>

    <h1 class="name">[ YOUR NAME ]</h1>
    <div class="role-line" id="typed"></div>

    <p class="summary">
      Product-minded engineer bridging user experience and platform reliability —
      from shaping personas, access-control models and business use cases, to building
      CI/CD pipelines, containerized deployments and infrastructure automation.
      <em>[ Replace with your own 2–3 line summary. ]</em>
    </p>

    <div class="contact">
      <a class="chip" href="mailto:you@email.com">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 7 10 6 10-6"/></svg>
        you@email.com
      </a>
      <a class="chip" href="tel:+910000000000">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92Z"/></svg>
        +91 00000 00000
      </a>
      <a class="chip" href="#">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-4 0v7h-4v-7a6 6 0 0 1 6-6Z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        linkedin.com/in/you
      </a>
      <a class="chip" href="#">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.4 5.4 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"/></svg>
        github.com/you
      </a>
      <span class="chip">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
        Vijayawada, IN
      </span>
    </div>
  </header>

  <!-- ================= METRICS ================= -->
  <section class="section">
    <div class="sec-head reveal">
      <span class="sec-idx">01</span>
      <span class="sec-title">At a Glance</span>
      <span class="sec-rule"></span>
    </div>
    <div class="panel reveal">
      <div class="metrics">
        <div class="metric">
          <div class="metric-num" data-count="5">0</div>
          <div class="metric-label">Years Experience</div>
        </div>
        <div class="metric">
          <div class="metric-num" data-count="12">0</div>
          <div class="metric-label">Projects Shipped</div>
        </div>
        <div class="metric">
          <div class="metric-num" data-count="5">0</div>
          <div class="metric-label">Core Modules Owned</div>
        </div>
        <div class="metric">
          <div class="metric-num" data-count="99" data-suffix="%">0</div>
          <div class="metric-label">Deploy Reliability</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= EXPERIENCE ================= -->
  <section class="section">
    <div class="sec-head reveal">
      <span class="sec-idx">02</span>
      <span class="sec-title">Experience</span>
      <span class="sec-rule"></span>
    </div>
    <div class="timeline">

      <article class="panel job reveal">
        <div class="job-when">2023 — Present<span class="now">// active</span></div>
        <div>
          <div class="job-role">[ Job Title — e.g. Product &amp; Platform Engineer ]</div>
          <div class="job-org">[ Company Name ]</div>
          <ul class="job-points">
            <li>Designed a scalable role / role-group access-control model spanning 5 product modules and 5 personas, cutting role sprawl from 60+ down to ~15.</li>
            <li>Authored delivery-planning templates and business use cases, aligning product, business and engineering stakeholders.</li>
            <li>Built and maintained multi-branch Jenkins CI/CD pipelines using shared Groovy libraries for build and deploy orchestration.</li>
            <li>[ Add a quantified achievement — impact, scale, or outcome. ]</li>
          </ul>
        </div>
      </article>

      <article class="panel job reveal">
        <div class="job-when">2021 — 2023</div>
        <div>
          <div class="job-role">[ Previous Job Title ]</div>
          <div class="job-org">[ Previous Company ]</div>
          <ul class="job-points">
            <li>Containerized application services with Docker, defining clean ENTRYPOINT / CMD startup contracts for reliable boots.</li>
            <li>Managed Kubernetes deployments via Helm charts across build and deploy environments.</li>
            <li>[ Add another responsibility or achievement here. ]</li>
          </ul>
        </div>
      </article>

      <article class="panel job reveal">
        <div class="job-when">2019 — 2021</div>
        <div>
          <div class="job-role">[ Earlier Job Title ]</div>
          <div class="job-org">[ Earlier Company ]</div>
          <ul class="job-points">
            <li>[ Describe a foundational responsibility or project. ]</li>
            <li>[ Add a measurable result if you have one. ]</li>
          </ul>
        </div>
      </article>

    </div>
  </section>

  <!-- ================= SKILLS ================= -->
  <section class="section">
    <div class="sec-head reveal">
      <span class="sec-idx">03</span>
      <span class="sec-title">Skill Matrix</span>
      <span class="sec-rule"></span>
    </div>
    <div class="panel reveal">
      <div class="skills-grid">

        <div>
          <div class="skill-cat">// Product &amp; Strategy</div>
          <div class="skill-row">
            <div class="skill-name"><span>Product Discovery</span><span>90</span></div>
            <div class="bar"><div class="bar-fill" data-w="90"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>User Personas &amp; Research</span><span>85</span></div>
            <div class="bar"><div class="bar-fill" data-w="85"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>Use-Case Modeling</span><span>88</span></div>
            <div class="bar"><div class="bar-fill" data-w="88"></div></div>
          </div>
        </div>

        <div>
          <div class="skill-cat">// Platform &amp; DevOps</div>
          <div class="skill-row">
            <div class="skill-name"><span>CI/CD — Jenkins</span><span>88</span></div>
            <div class="bar"><div class="bar-fill" data-w="88"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>Docker &amp; Containers</span><span>85</span></div>
            <div class="bar"><div class="bar-fill" data-w="85"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>Kubernetes &amp; Helm</span><span>78</span></div>
            <div class="bar"><div class="bar-fill" data-w="78"></div></div>
          </div>
        </div>

        <div>
          <div class="skill-cat">// Engineering</div>
          <div class="skill-row">
            <div class="skill-name"><span>Groovy / Scripting</span><span>80</span></div>
            <div class="bar"><div class="bar-fill" data-w="80"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>Git &amp; Version Control</span><span>90</span></div>
            <div class="bar"><div class="bar-fill" data-w="90"></div></div>
          </div>
          <div class="skill-row">
            <div class="skill-name"><span>System Design</span><span>82</span></div>
            <div class="bar"><div class="bar-fill" data-w="82"></div></div>
          </div>
        </div>

      </div>

      <div style="margin-top:24px;">
        <div class="skill-cat">// Toolbelt</div>
        <div class="tags">
          <span class="tag">Jenkins</span>
          <span class="tag">Docker</span>
          <span class="tag">Kubernetes</span>
          <span class="tag">Helm</span>
          <span class="tag">Groovy</span>
          <span class="tag">Git</span>
          <span class="tag">Linux</span>
          <span class="tag">REST APIs</span>
          <span class="tag">Figma</span>
          <span class="tag">Jira</span>
          <span class="tag">Confluence</span>
          <span class="tag">[ Add yours ]</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= PROJECTS + EDUCATION ================= -->
  <section class="section">
    <div class="sec-head reveal">
      <span class="sec-idx">04</span>
      <span class="sec-title">Selected Work &amp; Education</span>
      <span class="sec-rule"></span>
    </div>
    <div class="two-col">

      <div class="panel reveal">
        <div class="skill-cat">// Projects</div>
        <div style="margin-top:6px;">
          <div class="edu-item">
            <div class="edu-deg">Onjoi — Health &amp; Wellness Platform</div>
            <div class="edu-school">Product / Access-Control Design</div>
            <p style="color:var(--ink-soft);font-size:0.9rem;margin-top:6px;">
              Defined the role-group permission architecture across Water, Nutrition, Sleep,
              Stress &amp; Exercise modules — a scalable, stakeholder-friendly model.
            </p>
          </div>
          <div class="edu-item">
            <div class="edu-deg">CI/CD Shared Library Framework</div>
            <div class="edu-school">Platform Engineering</div>
            <p style="color:var(--ink-soft);font-size:0.9rem;margin-top:6px;">
              Reusable Groovy pipeline library orchestrating build &amp; deploy stages for
              multi-branch projects with Helm-based releases.
            </p>
          </div>
          <div class="edu-item">
            <div class="edu-deg">[ Your Project Name ]</div>
            <div class="edu-school">[ Category / Role ]</div>
            <p style="color:var(--ink-soft);font-size:0.9rem;margin-top:6px;">
              [ One-line description of impact or scope. ]
            </p>
          </div>
        </div>
      </div>

      <div class="panel reveal">
        <div class="skill-cat">// Education</div>
        <div style="margin-top:6px;">
          <div class="edu-item">
            <div class="edu-deg">[ Degree — e.g. B.Tech, Computer Science ]</div>
            <div class="edu-school">[ University / Institute ]</div>
            <div class="edu-meta">[ 20XX — 20XX ] · [ CGPA / % ]</div>
          </div>
          <div class="edu-item">
            <div class="edu-deg">[ Certification Name ]</div>
            <div class="edu-school">[ Issuing Body ]</div>
            <div class="edu-meta">[ Year ]</div>
          </div>
        </div>
        <div style="margin-top:16px;">
          <div class="skill-cat">// Languages</div>
          <div class="tags">
            <span class="tag">English</span>
            <span class="tag">Telugu</span>
            <span class="tag">Hindi</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <footer class="footer reveal">
    Built with HTML · CSS · JavaScript
    <span class="dot-sm">●</span>
    Press <strong>Ctrl/Cmd + P</strong> to export as PDF
    <span class="dot-sm">●</span>
    <span id="year"></span>
  </footer>

</div>

<script>
  /* ---------- Live UTC clock ---------- */
  function tickClock() {
    const d = new Date();
    const hh = String(d.getUTCHours()).padStart(2, '0');
    const mm = String(d.getUTCMinutes()).padStart(2, '0');
    const ss = String(d.getUTCSeconds()).padStart(2, '0');
    document.getElementById('clock').textContent = hh + ':' + mm + ':' + ss + ' UTC';
  }
  tickClock();
  setInterval(tickClock, 1000);

  document.getElementById('year').textContent = '© ' + new Date().getFullYear();

  /* ---------- Typewriter role line ---------- */
  const roles = [
    'Product & Platform Engineer',
    'CI/CD & DevOps Practitioner',
    'User-Experience Systems Thinker',
    '[ Customize these roles ]'
  ];
  const typed = document.getElementById('typed');
  let rIdx = 0, cIdx = 0, deleting = false;

  function typeLoop() {
    const word = roles[rIdx];
    if (!deleting) {
      cIdx++;
      if (cIdx > word.length) { deleting = true; setTimeout(typeLoop, 1600); return; }
    } else {
      cIdx--;
      if (cIdx === 0) { deleting = false; rIdx = (rIdx + 1) % roles.length; }
    }
    typed.innerHTML = word.substring(0, cIdx) + '<span class="cursor"></span>';
    setTimeout(typeLoop, deleting ? 45 : 85);
  }
  typeLoop();

  /* ---------- Scroll reveal ---------- */
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        entry.target.style.transitionDelay = (i % 4 * 0.08) + 's';
        entry.target.classList.add('in');
        io.unobserve(entry.target);

        /* trigger skill bars */
        entry.target.querySelectorAll('.bar-fill').forEach(bar => {
          bar.style.width = bar.dataset.w + '%';
        });
        /* trigger counters */
        entry.target.querySelectorAll('.metric-num').forEach(animateCount);
      }
    });
  }, { threshold: 0.18 });
  reveals.forEach(el => io.observe(el));

  /* ---------- Count-up metrics ---------- */
  function animateCount(el) {
    const target = parseInt(el.dataset.count, 10);
    const suffix = el.dataset.suffix || '';
    let cur = 0;
    const step = Math.max(1, Math.round(target / 38));
    const timer = setInterval(() => {
      cur += step;
      if (cur >= target) { cur = target; clearInterval(timer); }
      el.textContent = cur + suffix;
    }, 26);
  }

  /* ---------- Subtle parallax on orbs ---------- */
  window.addEventListener('mousemove', (e) => {
    const x = (e.clientX / window.innerWidth - 0.5) * 24;
    const y = (e.clientY / window.innerHeight - 0.5) * 24;
    document.querySelector('.orb-a').style.transform = 'translate(' + x + 'px,' + y + 'px)';
    document.querySelector('.orb-b').style.transform = 'translate(' + (-x) + 'px,' + (-y) + 'px)';
  });
</script>

</body>
</html>
