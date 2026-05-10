<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Hassan Aamir — AI Developer & ML Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Bebas+Neue&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #050a0e;
    --bg2: #0b1318;
    --bg3: #0f1c24;
    --neon: #00f5c4;
    --neon2: #00c2ff;
    --neon3: #ff4d6d;
    --text: #c8d8e4;
    --muted: #4a6070;
    --card: #0d1f2d;
    --border: #1a3040;
    --mono: 'Space Mono', monospace;
    --display: 'Bebas Neue', sans-serif;
    --body: 'DM Sans', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    overflow-x: hidden;
    cursor: none;
  }

  /* ── Custom Cursor ── */
  #cursor {
    position: fixed; z-index: 9999;
    width: 12px; height: 12px;
    background: var(--neon);
    border-radius: 50%;
    pointer-events: none;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: screen;
  }
  #cursor-ring {
    position: fixed; z-index: 9998;
    width: 36px; height: 36px;
    border: 1.5px solid var(--neon);
    border-radius: 50%;
    pointer-events: none;
    transform: translate(-50%, -50%);
    transition: transform 0.15s ease-out, width 0.3s, height 0.3s, opacity 0.3s;
    opacity: 0.5;
  }
  body:has(a:hover) #cursor, body:has(button:hover) #cursor { width: 20px; height: 20px; background: var(--neon3); }
  body:has(a:hover) #cursor-ring, body:has(button:hover) #cursor-ring { width: 52px; height: 52px; border-color: var(--neon3); }

  /* ── Scanline overlay ── */
  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 9990;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.04) 2px,
      rgba(0,0,0,0.04) 4px
    );
    pointer-events: none;
  }

  /* ── Nav ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    background: rgba(5,10,14,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: var(--mono); font-size: 0.85rem;
    color: var(--neon); letter-spacing: 0.05em;
  }
  .nav-logo span { color: var(--muted); }
  .nav-links { display: flex; gap: 2.5rem; }
  .nav-links a {
    font-family: var(--mono); font-size: 0.75rem; color: var(--muted);
    text-decoration: none; letter-spacing: 0.1em; text-transform: uppercase;
    position: relative; transition: color 0.2s;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1px; background: var(--neon);
    transition: width 0.3s;
  }
  .nav-links a:hover { color: var(--neon); }
  .nav-links a:hover::after { width: 100%; }

  /* ── Hero ── */
  #hero {
    min-height: 100vh;
    display: grid; place-items: center;
    position: relative; overflow: hidden;
    padding: 8rem 4rem 4rem;
  }

  .hero-grid-bg {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,245,196,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,196,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse at center, black 30%, transparent 80%);
  }

  .hero-glow {
    position: absolute;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,245,196,0.07) 0%, transparent 70%);
    top: 50%; left: 50%; transform: translate(-50%, -50%);
    animation: pulse-glow 4s ease-in-out infinite;
  }
  @keyframes pulse-glow {
    0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.7; }
    50% { transform: translate(-50%, -50%) scale(1.1); opacity: 1; }
  }

  .hero-content { position: relative; z-index: 1; max-width: 900px; }

  .hero-tag {
    display: inline-block;
    font-family: var(--mono); font-size: 0.75rem; color: var(--neon);
    border: 1px solid rgba(0,245,196,0.3); padding: 0.3rem 0.8rem;
    margin-bottom: 1.5rem; letter-spacing: 0.15em;
    animation: fadeUp 0.6s ease both;
  }

  .hero-name {
    font-family: var(--display);
    font-size: clamp(5rem, 12vw, 10rem);
    line-height: 0.92;
    letter-spacing: 0.02em;
    color: #fff;
    animation: fadeUp 0.6s 0.1s ease both;
  }
  .hero-name .accent { color: var(--neon); -webkit-text-stroke: 0px; }

  .hero-sub {
    font-size: 1.1rem; color: var(--muted); margin-top: 1.5rem;
    max-width: 520px; line-height: 1.7;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-badges {
    display: flex; flex-wrap: wrap; gap: 0.6rem;
    margin-top: 2rem;
    animation: fadeUp 0.6s 0.3s ease both;
  }
  .badge {
    font-family: var(--mono); font-size: 0.7rem;
    padding: 0.35rem 0.8rem;
    border: 1px solid var(--border);
    color: var(--text); letter-spacing: 0.08em;
    background: rgba(255,255,255,0.02);
  }

  .hero-cta {
    display: flex; gap: 1rem; margin-top: 3rem;
    animation: fadeUp 0.6s 0.4s ease both;
  }
  .btn-primary {
    font-family: var(--mono); font-size: 0.8rem;
    padding: 0.9rem 2rem; background: var(--neon);
    color: var(--bg); border: none; cursor: none;
    letter-spacing: 0.12em; text-transform: uppercase;
    text-decoration: none; display: inline-block;
    transition: background 0.2s, transform 0.15s;
    position: relative; overflow: hidden;
  }
  .btn-primary:hover { background: #00d4aa; transform: translateY(-2px); }
  .btn-secondary {
    font-family: var(--mono); font-size: 0.8rem;
    padding: 0.9rem 2rem; background: transparent;
    color: var(--neon); border: 1px solid rgba(0,245,196,0.4);
    cursor: none; letter-spacing: 0.12em; text-transform: uppercase;
    text-decoration: none; display: inline-block;
    transition: background 0.2s, transform 0.15s;
  }
  .btn-secondary:hover { background: rgba(0,245,196,0.06); transform: translateY(-2px); }

  .hero-stats {
    position: absolute; right: 4rem; top: 50%;
    transform: translateY(-50%);
    display: flex; flex-direction: column; gap: 2rem;
    animation: fadeUp 0.6s 0.5s ease both;
  }
  .stat { text-align: right; }
  .stat-num { font-family: var(--display); font-size: 2.8rem; color: var(--neon); line-height: 1; }
  .stat-label { font-family: var(--mono); font-size: 0.65rem; color: var(--muted); letter-spacing: 0.12em; margin-top: 0.2rem; }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── Section base ── */
  section { padding: 7rem 4rem; max-width: 1200px; margin: 0 auto; }
  .section-label {
    font-family: var(--mono); font-size: 0.7rem; color: var(--neon);
    letter-spacing: 0.2em; text-transform: uppercase; margin-bottom: 0.8rem;
    display: flex; align-items: center; gap: 1rem;
  }
  .section-label::before {
    content: ''; display: block; width: 30px; height: 1px; background: var(--neon);
  }
  .section-title {
    font-family: var(--display); font-size: clamp(2.5rem, 5vw, 4.5rem);
    color: #fff; line-height: 0.95; margin-bottom: 3rem;
  }

  /* ── Reveal animation ── */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── About ── */
  #about { border-top: 1px solid var(--border); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: start;
  }
  .about-text p {
    color: var(--text); font-size: 1rem; line-height: 1.85; margin-bottom: 1rem; font-weight: 300;
  }
  .about-text p strong { color: var(--neon); font-weight: 500; }
  .about-certs { display: flex; flex-direction: column; gap: 1rem; }
  .cert {
    border: 1px solid var(--border); padding: 1.2rem 1.5rem;
    background: var(--card);
    display: flex; align-items: center; gap: 1rem;
    position: relative; overflow: hidden;
    transition: border-color 0.3s, transform 0.2s;
  }
  .cert::before {
    content: ''; position: absolute; left: 0; top: 0; bottom: 0;
    width: 3px; background: var(--neon);
  }
  .cert:hover { border-color: rgba(0,245,196,0.4); transform: translateX(4px); }
  .cert-icon { font-size: 1.4rem; }
  .cert-body {}
  .cert-name { font-family: var(--mono); font-size: 0.75rem; color: #fff; font-weight: 700; }
  .cert-org { font-size: 0.8rem; color: var(--muted); margin-top: 0.2rem; }

  /* ── Skills ── */
  #skills { border-top: 1px solid var(--border); }
  .skills-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 0.8rem;
  }
  .skill-chip {
    border: 1px solid var(--border); background: var(--card);
    padding: 0.9rem 1rem; text-align: center;
    font-family: var(--mono); font-size: 0.72rem; color: var(--text);
    letter-spacing: 0.06em;
    position: relative; overflow: hidden;
    transition: border-color 0.3s, color 0.3s, transform 0.2s;
    cursor: default;
  }
  .skill-chip::after {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,245,196,0.06), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .skill-chip:hover { border-color: var(--neon); color: var(--neon); transform: translateY(-3px); }
  .skill-chip:hover::after { opacity: 1; }
  .skill-section-title {
    font-family: var(--mono); font-size: 0.7rem; color: var(--neon2);
    letter-spacing: 0.15em; margin: 2.5rem 0 1rem; text-transform: uppercase;
  }

  /* ── Projects ── */
  #projects { border-top: 1px solid var(--border); }
  .projects-filter {
    display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 3rem;
  }
  .filter-btn {
    font-family: var(--mono); font-size: 0.7rem; color: var(--muted);
    border: 1px solid var(--border); padding: 0.4rem 1rem;
    background: none; cursor: none; letter-spacing: 0.1em;
    transition: all 0.2s;
  }
  .filter-btn:hover, .filter-btn.active { border-color: var(--neon); color: var(--neon); }
  .filter-btn.active { background: rgba(0,245,196,0.06); }

  .projects-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(340px, 1fr)); gap: 1.2rem;
  }
  .project-card {
    border: 1px solid var(--border); background: var(--card);
    padding: 1.8rem; position: relative; overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    display: flex; flex-direction: column;
  }
  .project-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--neon), transparent);
    transform: scaleX(0); transition: transform 0.4s;
  }
  .project-card:hover { border-color: rgba(0,245,196,0.25); transform: translateY(-4px); }
  .project-card:hover::before { transform: scaleX(1); }

  .project-cat {
    font-family: var(--mono); font-size: 0.62rem; color: var(--neon2);
    letter-spacing: 0.15em; text-transform: uppercase; margin-bottom: 0.8rem;
  }
  .project-title {
    font-family: var(--mono); font-size: 0.9rem; color: #fff;
    font-weight: 700; line-height: 1.4; margin-bottom: 0.8rem;
  }
  .project-desc {
    font-size: 0.82rem; color: var(--muted); line-height: 1.65; flex: 1;
  }
  .project-tags {
    display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 1.3rem;
  }
  .project-tag {
    font-family: var(--mono); font-size: 0.6rem; color: var(--muted);
    border: 1px solid var(--border); padding: 0.2rem 0.5rem;
  }
  .project-link {
    display: inline-flex; align-items: center; gap: 0.4rem;
    margin-top: 1.3rem; font-family: var(--mono); font-size: 0.7rem;
    color: var(--neon); text-decoration: none;
    transition: gap 0.2s;
  }
  .project-link:hover { gap: 0.7rem; }
  .project-link::after { content: '→'; }
  .flagship-badge {
    position: absolute; top: 1.2rem; right: 1.2rem;
    font-family: var(--mono); font-size: 0.55rem; color: var(--neon3);
    border: 1px solid var(--neon3); padding: 0.2rem 0.5rem; letter-spacing: 0.1em;
  }

  /* ── Contact ── */
  #contact {
    border-top: 1px solid var(--border);
    text-align: center; padding: 8rem 4rem;
  }
  .contact-wrap { max-width: 600px; margin: 0 auto; }
  .contact-big {
    font-family: var(--display); font-size: clamp(3rem, 8vw, 7rem);
    color: #fff; line-height: 0.92; margin-bottom: 1.5rem;
  }
  .contact-big .accent { color: var(--neon); }
  .contact-sub { font-size: 1rem; color: var(--muted); margin-bottom: 2.5rem; line-height: 1.7; }
  .contact-email {
    display: inline-block; font-family: var(--mono); font-size: 0.85rem;
    color: var(--neon); border-bottom: 1px solid rgba(0,245,196,0.4);
    text-decoration: none; padding-bottom: 0.3rem;
    transition: border-color 0.2s;
  }
  .contact-email:hover { border-color: var(--neon); }
  .social-links { display: flex; gap: 1.5rem; justify-content: center; margin-top: 2.5rem; }
  .social-link {
    font-family: var(--mono); font-size: 0.7rem; color: var(--muted);
    text-decoration: none; letter-spacing: 0.12em;
    border: 1px solid var(--border); padding: 0.6rem 1.4rem;
    transition: all 0.2s;
  }
  .social-link:hover { color: var(--neon); border-color: rgba(0,245,196,0.4); }

  /* ── Footer ── */
  footer {
    border-top: 1px solid var(--border); padding: 2rem 4rem;
    display: flex; align-items: center; justify-content: space-between;
  }
  footer p { font-family: var(--mono); font-size: 0.65rem; color: var(--muted); }

  /* ── Terminal block ── */
  .terminal {
    background: #040d12; border: 1px solid var(--border);
    padding: 1.5rem 2rem; margin-top: 2rem; font-family: var(--mono);
    font-size: 0.78rem; line-height: 2;
    position: relative;
  }
  .terminal::before {
    content: '● ● ●'; position: absolute; top: 0.8rem; left: 1rem;
    font-size: 0.6rem; color: var(--muted); letter-spacing: 0.4em;
  }
  .term-line { padding-top: 1rem; }
  .term-prompt { color: var(--neon); }
  .term-output { color: var(--muted); }
  .term-val { color: var(--neon2); }

  /* ── Responsive ── */
  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    section { padding: 5rem 1.5rem; }
    #hero { padding: 7rem 1.5rem 3rem; }
    .hero-stats { position: static; transform: none; flex-direction: row; margin-top: 3rem; }
    .hero-content { max-width: 100%; }
    .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
    .projects-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 0.5rem; }
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo"><span>// </span>hassan_aamir.dev</div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </div>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="hero-grid-bg"></div>
  <div class="hero-glow"></div>
  <div class="hero-content">
    <div class="hero-tag">// AI Developer &amp; ML Engineer</div>
    <h1 class="hero-name">HASSAN<br><span class="accent">AAMIR</span></h1>
    <p class="hero-sub">
      Computer Science graduate from NUST, Islamabad — building intelligent systems at the intersection of machine learning, full-stack engineering, and data science.
    </p>
    <div class="hero-badges">
      <span class="badge">IBM Certified AI Developer</span>
      <span class="badge">Stanford ML Specialist</span>
      <span class="badge">Imperial College London · Math for ML</span>
    </div>
    <div class="hero-cta">
      <a href="#projects" class="btn-primary">View Projects</a>
      <a href="#contact" class="btn-secondary">Get in Touch</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">30+</div>
      <div class="stat-label">Projects</div>
    </div>
    <div class="stat">
      <div class="stat-num">3</div>
      <div class="stat-label">Certifications</div>
    </div>
    <div class="stat">
      <div class="stat-num">14+</div>
      <div class="stat-label">Technologies</div>
    </div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-label reveal">001 — About</div>
  <div class="section-title reveal">Who I <span style="color:var(--neon)">Am</span></div>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>
        I'm a <strong>B.Sc. Computer Science</strong> graduate from <strong>NUST, Islamabad</strong> with a deep focus on AI, machine learning, and full-stack development. I love building systems that are not just functional — but genuinely intelligent.
      </p>
      <p>
        My professional experience spans <strong>AngularJS, NestJS, and Prisma ORM</strong> in production environments. Outside of work, I've shipped over 30 projects ranging from computer vision pipelines and LLM-powered assistants to web scrapers and interactive data dashboards.
      </p>
      <p>
        I believe great software sits at the intersection of elegant code, thoughtful UX, and purposeful AI — and I'm always pushing to create exactly that.
      </p>
      <div class="terminal">
        <div class="term-line">
          <span class="term-prompt">$ </span><span class="term-output">cat education.json</span>
        </div>
        <div class="term-line">
          <span class="term-val">&gt; NUST Islamabad — B.Sc. Computer Science</span>
        </div>
        <div class="term-line">
          <span class="term-prompt">$ </span><span class="term-output">echo $location</span>
        </div>
        <div class="term-line">
          <span class="term-val">&gt; Pakistan 🇵🇰</span>
        </div>
      </div>
    </div>
    <div class="about-certs reveal">
      <div class="cert">
        <div class="cert-icon">🤖</div>
        <div class="cert-body">
          <div class="cert-name">AI Developer Professional</div>
          <div class="cert-org">IBM Certified</div>
        </div>
      </div>
      <div class="cert">
        <div class="cert-icon">🎓</div>
        <div class="cert-body">
          <div class="cert-name">Machine Learning Specialization</div>
          <div class="cert-org">Stanford University</div>
        </div>
      </div>
      <div class="cert">
        <div class="cert-icon">📐</div>
        <div class="cert-body">
          <div class="cert-name">Mathematics for ML Specialization</div>
          <div class="cert-org">Imperial College London</div>
        </div>
      </div>
      <div class="cert" style="--neon: var(--neon2)">
        <div class="cert-icon">💼</div>
        <div class="cert-body">
          <div class="cert-name">Industry Experience</div>
          <div class="cert-org">AngularJS · NestJS · Prisma ORM</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label reveal">002 — Stack</div>
  <div class="section-title reveal">My <span style="color:var(--neon)">Skills</span></div>

  <div class="reveal">
    <div class="skill-section-title">// AI &amp; Machine Learning</div>
    <div class="skills-grid">
      <div class="skill-chip">TensorFlow</div>
      <div class="skill-chip">PyTorch</div>
      <div class="skill-chip">Scikit-Learn</div>
      <div class="skill-chip">LangChain</div>
      <div class="skill-chip">IBM Watson</div>
      <div class="skill-chip">YOLOv8</div>
      <div class="skill-chip">BLIP Model</div>
      <div class="skill-chip">RAG Systems</div>
    </div>

    <div class="skill-section-title">// Languages</div>
    <div class="skills-grid">
      <div class="skill-chip">Python</div>
      <div class="skill-chip">JavaScript</div>
      <div class="skill-chip">TypeScript</div>
      <div class="skill-chip">C</div>
      <div class="skill-chip">C++</div>
      <div class="skill-chip">Java</div>
    </div>

    <div class="skill-section-title">// Full Stack</div>
    <div class="skills-grid">
      <div class="skill-chip">React.js</div>
      <div class="skill-chip">Node.js</div>
      <div class="skill-chip">NestJS</div>
      <div class="skill-chip">Flask</div>
      <div class="skill-chip">AngularJS</div>
      <div class="skill-chip">Tailwind CSS</div>
      <div class="skill-chip">Vite</div>
      <div class="skill-chip">HTML / CSS</div>
    </div>

    <div class="skill-section-title">// Data &amp; Infra</div>
    <div class="skills-grid">
      <div class="skill-chip">PostgreSQL</div>
      <div class="skill-chip">MySQL</div>
      <div class="skill-chip">MongoDB</div>
      <div class="skill-chip">Prisma ORM</div>
      <div class="skill-chip">Docker</div>
      <div class="skill-chip">Apache Spark</div>
      <div class="skill-chip">HDFS</div>
      <div class="skill-chip">Linux</div>
    </div>

    <div class="skill-section-title">// Scraping &amp; Automation</div>
    <div class="skills-grid">
      <div class="skill-chip">BeautifulSoup</div>
      <div class="skill-chip">Scrapy</div>
      <div class="skill-chip">Selenium</div>
      <div class="skill-chip">Pandas</div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label reveal">003 — Work</div>
  <div class="section-title reveal">Featured <span style="color:var(--neon)">Projects</span></div>

  <div class="projects-filter reveal" id="filter-bar">
    <button class="filter-btn active" data-cat="all">All</button>
    <button class="filter-btn" data-cat="AI">AI Dev</button>
    <button class="filter-btn" data-cat="ML">Machine Learning</button>
    <button class="filter-btn" data-cat="CV">Computer Vision</button>
    <button class="filter-btn" data-cat="FS">Full Stack</button>
    <button class="filter-btn" data-cat="WS">Web Scraping</button>
  </div>

  <div class="projects-grid reveal" id="projects-grid">

    <div class="project-card" data-cat="FS AI">
      <div class="flagship-badge">★ FLAGSHIP</div>
      <div class="project-cat">Full Stack · AI</div>
      <div class="project-title">AI-Powered Annual Budget Creator</div>
      <div class="project-desc">Production-grade financial planning app with intelligent AI insights, built with React, NestJS, TypeScript, PostgreSQL, and Prisma. Deployed on AWS Amplify.</div>
      <div class="project-tags">
        <span class="project-tag">ReactJS</span>
        <span class="project-tag">NestJS</span>
        <span class="project-tag">TypeScript</span>
        <span class="project-tag">PostgreSQL</span>
        <span class="project-tag">Prisma</span>
      </div>
      <a class="project-link" href="https://master.d7rdp3159yz1h.amplifyapp.com/" target="_blank">Live Demo</a>
    </div>

    <div class="project-card" data-cat="FS AI">
      <div class="flagship-badge">★ FLAGSHIP</div>
      <div class="project-cat">Full Stack · AI</div>
      <div class="project-title">Virtual Job Assistant</div>
      <div class="project-desc">End-to-end AI career platform that analyzes resumes, generates job-match reports, and provides personalized recommendations. Full CRUD with PDF export.</div>
      <div class="project-tags">
        <span class="project-tag">React</span>
        <span class="project-tag">Vite</span>
        <span class="project-tag">Flask</span>
        <span class="project-tag">MySQL</span>
        <span class="project-tag">ReportLab</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/Virtual-Job-Assistant" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="CV">
      <div class="project-cat">Computer Vision</div>
      <div class="project-title">Crime Detection Pipeline</div>
      <div class="project-desc">Real-time anomaly and crime detection system using YOLOv8 for object detection, ByteTrack for multi-object tracking, and 3D CNN for temporal action recognition.</div>
      <div class="project-tags">
        <span class="project-tag">YOLOv8</span>
        <span class="project-tag">ByteTrack</span>
        <span class="project-tag">3D CNN</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/crime_detection_system" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="AI">
      <div class="project-cat">AI Development</div>
      <div class="project-title">RAG Personal Data Chatbot</div>
      <div class="project-desc">AI chatbot that answers questions about your own documents using Retrieval-Augmented Generation, IBM Watson, and a Flask API with a custom HTML/JS frontend.</div>
      <div class="project-tags">
        <span class="project-tag">RAG</span>
        <span class="project-tag">IBM Watson</span>
        <span class="project-tag">Flask</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/personal_data_assistant" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="AI">
      <div class="project-cat">AI Development</div>
      <div class="project-title">Voice Chat with GPT</div>
      <div class="project-desc">Full voice-to-voice conversational AI using OpenAI GPT, IBM Watson Speech-to-Text and Text-to-Speech, enabling natural spoken conversations in the browser.</div>
      <div class="project-tags">
        <span class="project-tag">OpenAI GPT</span>
        <span class="project-tag">IBM Watson STT/TTS</span>
        <span class="project-tag">Python</span>
        <span class="project-tag">HTML/CSS/JS</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/Chatbot-With-Voice-And-OpenAI" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="AI">
      <div class="project-cat">AI Development</div>
      <div class="project-title">Meeting Summariser</div>
      <div class="project-desc">Automatically transcribes and summarises meetings using IBM Watson STT and LLAMA LLM, surfaced through an intuitive Gradio interface.</div>
      <div class="project-tags">
        <span class="project-tag">LLAMA</span>
        <span class="project-tag">IBM Watson</span>
        <span class="project-tag">Gradio</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/Meeting-Summariser/" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="AI">
      <div class="project-cat">AI Development</div>
      <div class="project-title">AI Career Coach</div>
      <div class="project-desc">Personalized AI career coaching tool powered by IBM Granite Model, helping users navigate career transitions and skill development with tailored advice.</div>
      <div class="project-tags">
        <span class="project-tag">IBM Granite</span>
        <span class="project-tag">Gradio</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/AI-Career-Coach" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="AI">
      <div class="project-cat">AI Development</div>
      <div class="project-title">Image Captioner</div>
      <div class="project-desc">Generates descriptive captions for uploaded images using the BLIP (Bootstrapped Language-Image Pretraining) vision-language model.</div>
      <div class="project-tags">
        <span class="project-tag">BLIP</span>
        <span class="project-tag">HuggingFace</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/image_captioner" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="ML">
      <div class="project-cat">Machine Learning</div>
      <div class="project-title">AutoML Platform</div>
      <div class="project-desc">A no-code UI-based AutoML tool offering 7 distinct ML models — Logistic Regression, SVM, Decision Tree, Random Forest, KNN, Naive Bayes, and Neural Networks — with live visualizations.</div>
      <div class="project-tags">
        <span class="project-tag">Scikit-Learn</span>
        <span class="project-tag">Python</span>
        <span class="project-tag">TensorFlow</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/CS245_Project_AutoMl" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="ML">
      <div class="project-cat">AI · Algorithms</div>
      <div class="project-title">AI Scheduling Solver</div>
      <div class="project-desc">Implements and benchmarks MCTS, CSPs, and Genetic Algorithms to solve complex multi-constraint scheduling problems — comparing performance across approaches.</div>
      <div class="project-tags">
        <span class="project-tag">MCTS</span>
        <span class="project-tag">CSP</span>
        <span class="project-tag">Genetic Algorithm</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/Scheduling-Solutions-using-Fundamental-AI-Algorithms" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="WS">
      <div class="project-cat">Web Scraping</div>
      <div class="project-title">Daraz.pk Product Hunter</div>
      <div class="project-desc">Scrapes and ranks top-selling products from Daraz.pk (Pakistan's largest e-commerce platform) using BeautifulSoup and Selenium for dynamic content.</div>
      <div class="project-tags">
        <span class="project-tag">BeautifulSoup</span>
        <span class="project-tag">Selenium</span>
        <span class="project-tag">Python</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/Daraz-product-hunter" target="_blank">GitHub</a>
    </div>

    <div class="project-card" data-cat="FS">
      <div class="project-cat">Full Stack</div>
      <div class="project-title">Court Booking Dashboard</div>
      <div class="project-desc">A real-time sports court reservation system with an elegant dashboard, slot management, and notifications — built with ReactJS, NestJS, and Prisma ORM.</div>
      <div class="project-tags">
        <span class="project-tag">ReactJS</span>
        <span class="project-tag">NestJS</span>
        <span class="project-tag">Prisma</span>
      </div>
      <a class="project-link" href="https://github.com/hassan2-aamir/court-booking-app" target="_blank">GitHub</a>
    </div>

  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-wrap">
    <div class="section-label reveal" style="justify-content:center">004 — Contact</div>
    <div class="contact-big reveal">LET'S<br><span class="accent">BUILD</span><br>TOGETHER</div>
    <p class="contact-sub reveal">
      Open to AI research roles, full-stack opportunities, and interesting collaborations. Drop me a message — I reply fast.
    </p>
    <a href="mailto:haamir.bscs23seecs@seecs.edu.pk" class="contact-email reveal">
      haamir.bscs23seecs@seecs.edu.pk
    </a>
    <div class="social-links reveal">
      <a class="social-link" href="https://www.github.com/hassan2-aamir" target="_blank">GitHub ↗</a>
      <a class="social-link" href="https://www.linkedin.com/in/hassan--aamir" target="_blank">LinkedIn ↗</a>
    </div>
  </div>
</section>

<footer>
  <p>© 2025 Hassan Aamir — AI Developer & ML Engineer</p>
  <p style="font-family:var(--mono);font-size:0.65rem;color:var(--muted)">Built with HTML · CSS · JS</p>
</footer>

<script>
  // ── Custom Cursor ──
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursor-ring');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();

  // ── Scroll reveal ──
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => io.observe(el));

  // ── Project filter ──
  const filterBtns = document.querySelectorAll('.filter-btn');
  const cards = document.querySelectorAll('.project-card');
  filterBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      filterBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const cat = btn.dataset.cat;
      cards.forEach(card => {
        const cats = card.dataset.cat || '';
        if (cat === 'all' || cats.includes(cat)) {
          card.style.display = '';
          card.style.animation = 'fadeUp 0.4s ease both';
        } else {
          card.style.display = 'none';
        }
      });
    });
  });

  // ── Typing effect in hero tag ──
  const tag = document.querySelector('.hero-tag');
  const original = tag.textContent;
  tag.textContent = '// ';
  let i = 3;
  const type = () => {
    if (i < original.length) {
      tag.textContent += original[i++];
      setTimeout(type, 45);
    }
  };
  setTimeout(type, 600);
</script>
</body>
</html>
