<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>notramos · Sergio Guntur</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323:wght@400&display=swap');

  :root {
    --black: #0a0a0f;
    --dark: #12121e;
    --panel: #1a1a2e;
    --border: #2a2a4a;
    --cyan: #00f5ff;
    --yellow: #ffe500;
    --pink: #ff2d78;
    --green: #39ff14;
    --orange: #ff6b2b;
    --purple: #b044ff;
    --white: #e8e8ff;
    --muted: #6a6a9a;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'VT323', monospace;
    font-size: 20px;
    line-height: 1.5;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Scanlines overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
  }

  /* ===== HERO ===== */
  .hero {
    text-align: center;
    padding: 3rem 0 2rem;
    position: relative;
  }

  .hero-stars {
    position: absolute;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
  }

  .star {
    position: absolute;
    width: 2px; height: 2px;
    background: var(--white);
    animation: twinkle var(--d, 2s) var(--delay, 0s) infinite;
  }

  @keyframes twinkle {
    0%, 100% { opacity: 0.1; }
    50% { opacity: 1; }
  }

  .title-box {
    display: inline-block;
    border: 3px solid var(--cyan);
    box-shadow: 0 0 20px var(--cyan), inset 0 0 20px rgba(0,245,255,0.05);
    padding: 1.5rem 2.5rem;
    position: relative;
    animation: borderPulse 3s ease-in-out infinite;
  }

  @keyframes borderPulse {
    0%, 100% { box-shadow: 0 0 20px var(--cyan), inset 0 0 20px rgba(0,245,255,0.05); }
    50% { box-shadow: 0 0 40px var(--cyan), 0 0 80px rgba(0,245,255,0.3), inset 0 0 30px rgba(0,245,255,0.1); }
  }

  .title-corner {
    position: absolute;
    width: 10px; height: 10px;
    background: var(--cyan);
  }
  .title-corner.tl { top: -3px; left: -3px; }
  .title-corner.tr { top: -3px; right: -3px; }
  .title-corner.bl { bottom: -3px; left: -3px; }
  .title-corner.br { bottom: -3px; right: -3px; }

  .pixel-name {
    font-family: 'Press Start 2P', monospace;
    font-size: clamp(18px, 3vw, 28px);
    color: var(--cyan);
    letter-spacing: 4px;
    text-shadow: 0 0 10px var(--cyan);
    display: block;
    animation: textGlow 2s ease-in-out infinite;
  }

  @keyframes textGlow {
    0%, 100% { text-shadow: 0 0 10px var(--cyan); }
    50% { text-shadow: 0 0 20px var(--cyan), 0 0 40px var(--cyan); }
  }

  .pixel-handle {
    font-family: 'Press Start 2P', monospace;
    font-size: clamp(10px, 1.5vw, 13px);
    color: var(--yellow);
    letter-spacing: 2px;
    display: block;
    margin-top: 0.75rem;
    text-shadow: 0 0 8px var(--yellow);
  }

  .subtitle {
    font-family: 'VT323', monospace;
    font-size: 22px;
    color: var(--green);
    margin-top: 0.5rem;
    display: block;
    letter-spacing: 1px;
  }

  /* Blinking cursor */
  .cursor::after {
    content: '█';
    animation: blink 1s step-start infinite;
    color: var(--cyan);
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ===== BADGES ROW ===== */
  .badges {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
    margin-top: 1.5rem;
  }

  .badge {
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    padding: 6px 12px;
    border: 2px solid;
    letter-spacing: 1px;
    animation: badgePop 0.4s var(--delay,0s) both;
  }

  @keyframes badgePop {
    from { transform: scale(0); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  .badge-cyan  { border-color: var(--cyan);   color: var(--cyan);   box-shadow: 0 0 8px var(--cyan); }
  .badge-pink  { border-color: var(--pink);   color: var(--pink);   box-shadow: 0 0 8px var(--pink); }
  .badge-green { border-color: var(--green);  color: var(--green);  box-shadow: 0 0 8px var(--green); }

  /* ===== SECTION ===== */
  .section {
    margin-top: 2.5rem;
    border: 2px solid var(--border);
    padding: 1.25rem 1.5rem;
    position: relative;
    background: var(--panel);
  }

  .section-label {
    position: absolute;
    top: -14px;
    left: 16px;
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    padding: 2px 10px;
    letter-spacing: 1px;
  }

  .sl-cyan   { background: var(--black); color: var(--cyan);   border: 2px solid var(--cyan);   box-shadow: 0 0 10px var(--cyan); }
  .sl-yellow { background: var(--black); color: var(--yellow); border: 2px solid var(--yellow); box-shadow: 0 0 10px var(--yellow); }
  .sl-pink   { background: var(--black); color: var(--pink);   border: 2px solid var(--pink);   box-shadow: 0 0 10px var(--pink); }
  .sl-green  { background: var(--black); color: var(--green);  border: 2px solid var(--green);  box-shadow: 0 0 10px var(--green); }
  .sl-purple { background: var(--black); color: var(--purple); border: 2px solid var(--purple); box-shadow: 0 0 10px var(--purple); }

  /* ===== TERMINAL BLOCK ===== */
  .terminal {
    background: #060610;
    border: 1px solid var(--border);
    padding: 1rem 1.25rem;
    font-family: 'VT323', monospace;
    font-size: 20px;
    line-height: 1.7;
  }

  .prompt { color: var(--green); }
  .cmd    { color: var(--white); }
  .out    { color: var(--muted); padding-left: 1rem; }
  .out-hi { color: var(--cyan); padding-left: 1rem; }

  /* ===== SKILL GRID ===== */
  .skill-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 12px;
    margin-top: 0.5rem;
  }

  .skill-card {
    border: 2px solid var(--c, var(--cyan));
    padding: 12px 8px;
    text-align: center;
    position: relative;
    overflow: hidden;
    cursor: default;
    transition: transform 0.15s, box-shadow 0.15s;
    background: rgba(0,0,0,0.4);
  }

  .skill-card:hover {
    transform: translateY(-3px) scale(1.03);
    box-shadow: 0 0 16px var(--c, var(--cyan));
  }

  .skill-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--c, var(--cyan));
    opacity: 0;
    transition: opacity 0.15s;
  }
  .skill-card:hover::before { opacity: 0.07; }

  .skill-icon {
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    color: var(--c, var(--cyan));
    display: block;
    margin-bottom: 6px;
    letter-spacing: 1px;
  }

  .skill-name {
    font-family: 'VT323', monospace;
    font-size: 22px;
    color: var(--white);
    display: block;
    letter-spacing: 1px;
  }

  .skill-lvl {
    display: flex;
    justify-content: center;
    gap: 3px;
    margin-top: 6px;
  }

  .lvl-pip {
    width: 8px; height: 8px;
    border: 1px solid var(--c, var(--cyan));
  }
  .lvl-pip.filled { background: var(--c, var(--cyan)); }

  /* ===== STATS ===== */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 12px;
    margin-top: 0.5rem;
  }

  .stat-box {
    border: 2px solid var(--c, var(--cyan));
    padding: 1rem;
    text-align: center;
    background: rgba(0,0,0,0.5);
    position: relative;
    overflow: hidden;
  }

  .stat-box::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: var(--c, var(--cyan));
    animation: scanbar 3s linear infinite;
  }

  @keyframes scanbar {
    0%   { transform: scaleX(0); transform-origin: left; }
    50%  { transform: scaleX(1); transform-origin: left; }
    51%  { transform: scaleX(1); transform-origin: right; }
    100% { transform: scaleX(0); transform-origin: right; }
  }

  .stat-label {
    font-family: 'Press Start 2P', monospace;
    font-size: 7px;
    color: var(--muted);
    letter-spacing: 1px;
    display: block;
    margin-bottom: 8px;
  }

  .stat-value {
    font-family: 'Press Start 2P', monospace;
    font-size: 22px;
    color: var(--c, var(--cyan));
    display: block;
    text-shadow: 0 0 12px var(--c, var(--cyan));
    animation: countUp 1s var(--delay, 0s) both;
  }

  @keyframes countUp {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .stat-sub {
    font-family: 'VT323', monospace;
    font-size: 16px;
    color: var(--muted);
    display: block;
    margin-top: 4px;
  }

  /* ===== CODE BLOCK ===== */
  .code-block {
    background: #060610;
    border: 1px solid var(--border);
    border-left: 3px solid var(--orange);
    padding: 1rem 1.25rem;
    font-family: 'VT323', monospace;
    font-size: 19px;
    line-height: 1.7;
    overflow-x: auto;
  }

  .c-keyword  { color: var(--pink); }
  .c-type     { color: var(--cyan); }
  .c-func     { color: var(--yellow); }
  .c-str      { color: var(--green); }
  .c-num      { color: var(--orange); }
  .c-comment  { color: #444470; font-style: italic; }
  .c-plain    { color: var(--white); }

  /* ===== CONTACT ===== */
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 12px;
    border: 2px solid var(--border);
    padding: 12px 16px;
    transition: border-color 0.2s, box-shadow 0.2s;
    background: rgba(0,0,0,0.3);
    text-decoration: none;
  }

  .contact-item:hover {
    border-color: var(--cyan);
    box-shadow: 0 0 12px var(--cyan);
  }

  .contact-icon {
    font-family: 'Press Start 2P', monospace;
    font-size: 10px;
    color: var(--cyan);
    min-width: 28px;
  }

  .contact-text {
    font-family: 'VT323', monospace;
    font-size: 20px;
    color: var(--white);
  }

  /* ===== FOOTER ===== */
  .footer {
    text-align: center;
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 1px solid var(--border);
  }

  .footer-quote {
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 2px;
    line-height: 2;
  }

  .footer-quote span {
    color: var(--yellow);
  }

  /* Retro pixel divider */
  .pixel-divider {
    display: flex;
    align-items: center;
    gap: 8px;
    margin: 2rem 0;
    color: var(--border);
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    letter-spacing: 3px;
  }
  .pixel-divider::before,
  .pixel-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* Scroll reveal */
  .reveal {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.5s, transform 0.5s;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Marquee */
  .marquee-wrap {
    overflow: hidden;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 8px 0;
    margin: 1.5rem 0;
    background: rgba(0,245,255,0.03);
  }

  .marquee-track {
    display: flex;
    gap: 40px;
    animation: marquee 20s linear infinite;
    white-space: nowrap;
  }

  @keyframes marquee {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  .marquee-item {
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    color: var(--muted);
    letter-spacing: 2px;
    flex-shrink: 0;
  }

  .marquee-item span { color: var(--cyan); margin-right: 6px; }
</style>
</head>
<body>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-stars" id="stars"></div>

    <div class="title-box">
      <div class="title-corner tl"></div>
      <div class="title-corner tr"></div>
      <div class="title-corner bl"></div>
      <div class="title-corner br"></div>
      <span class="pixel-name">SERGIO GUNTUR</span>
      <span class="pixel-handle">// notramos</span>
      <span class="subtitle">SOFTWARE DEVELOPER<span class="cursor"></span></span>
    </div>

    <div class="badges" style="margin-top:1.5rem;">
      <div class="badge badge-cyan"  style="--delay:0.1s">BACKEND</div>
      <div class="badge badge-pink"  style="--delay:0.2s">FULLSTACK</div>
      <div class="badge badge-green" style="--delay:0.3s">OPEN TO WORK</div>
      <div class="badge badge-cyan"  style="--delay:0.4s">WIB / UTC+7</div>
    </div>
  </div>

  <!-- MARQUEE -->
  <div class="marquee-wrap">
    <div class="marquee-track" id="marquee"></div>
  </div>

  <!-- ABOUT -->
  <div class="section reveal" style="border-color:#00f5ff30;">
    <span class="section-label sl-cyan">PLAYER INFO</span>
    <div class="terminal">
      <div><span class="prompt">$</span> <span class="cmd">cat about.txt</span></div>
      <div class="out-hi">─────────────────────────────────────</div>
      <div class="out">Name    : Sergio Guntur</div>
      <div class="out">Handle  : <span style="color:var(--yellow)">notramos</span></div>
      <div class="out">Degree  : S.Kom — Sistem Informasi</div>
      <div class="out">Role    : <span style="color:var(--cyan)">Backend-leaning fullstack developer</span></div>
      <div class="out">Focus   : Clean architecture, scalable APIs</div>
      <div class="out">Motto   : Build it. Break it. Make it fast.</div>
      <div class="out-hi">─────────────────────────────────────</div>
      <div style="margin-top:8px;"><span class="prompt">$</span> <span class="cmd">status --current</span></div>
      <div class="out">↳ Deepening Go concurrency patterns</div>
      <div class="out">↳ Exploring clean arch in PHP (Laravel)</div>
      <div class="out">↳ Containerizing everything with Docker</div>
      <div class="out">↳ DSA grind with C <span style="color:var(--green)">// never stops</span></div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section reveal" style="border-color:#ffe50030; margin-top:2.5rem;">
    <span class="section-label sl-yellow">SKILL TREE</span>
    <div class="skill-grid" id="skillGrid"></div>
  </div>

  <!-- STATS -->
  <div class="section reveal" style="border-color:#ff2d7830; margin-top:2.5rem;">
    <span class="section-label sl-pink">STATS</span>
    <div class="stats-row" id="statsRow"></div>
    <div style="margin-top:16px; text-align:center;">
      <img
        src="https://streak-stats.demolab.com?user=notramos&theme=dark-green&hide_border=true&background=060610&ring=00f5ff&fire=ff2d78&currStreakLabel=ffe500&stroke=2a2a4a&dates=6a6a9a"
        style="max-width:100%; border: 2px solid #2a2a4a;"
        alt="streak"
      />
    </div>
  </div>

  <!-- ORIGIN CODE -->
  <div class="section reveal" style="border-color:#ff6b2b30; margin-top:2.5rem;">
    <span class="section-label sl-pink" style="color:var(--orange); border-color:var(--orange); box-shadow: 0 0 10px var(--orange);">ORIGIN STORY</span>
    <div style="font-family:'VT323',monospace; font-size:19px; color:var(--muted); margin-bottom:12px;">
      The first program I ever wrote:
    </div>
    <div class="code-block">
<span class="c-comment">/* hello_world.c — where it all started */</span>
<span class="c-keyword">#include</span> <span class="c-str">&lt;stdio.h&gt;</span>

<span class="c-type">int</span> <span class="c-func">main</span><span class="c-plain">() {</span>
  <span class="c-func">printf</span><span class="c-plain">(</span><span class="c-str">"Hello, Dunia!\n"</span><span class="c-plain">);</span>
  <span class="c-keyword">return</span> <span class="c-num">0</span><span class="c-plain">;</span>
<span class="c-plain">}</span>
    </div>
    <div class="terminal" style="margin-top:10px;">
      <div><span class="prompt">$</span> <span class="cmd">gcc hello_world.c -o hello && ./hello</span></div>
      <div class="out" style="color:var(--green);">Hello, Dunia!</div>
      <div style="margin-top:4px;"><span class="prompt">$</span> <span class="cmd">echo "Simple. Correct. Ship it."</span></div>
      <div class="out" style="color:var(--yellow);">Simple. Correct. Ship it.</div>
    </div>
  </div>

  <!-- CONTACT -->
  <div class="section reveal" style="border-color:#39ff1430; margin-top:2.5rem;">
    <span class="section-label sl-green">CONTACT</span>
    <div class="contact-grid">
      <a href="https://github.com/notramos" class="contact-item" target="_blank">
        <span class="contact-icon">GH</span>
        <span class="contact-text">github.com/notramos</span>
      </a>
      <div class="contact-item">
        <span class="contact-icon" style="color:var(--yellow)">@</span>
        <span class="contact-text">open to opportunities</span>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer reveal">
    <div class="pixel-divider">★ EOF ★</div>
    <p class="footer-quote">
      "STAY HUNGRY"<br/>
      — <span>SERGIO GUNTUR</span> · 2025
    </p>
    <div style="margin-top:1.5rem; font-family:'Press Start 2P',monospace; font-size:7px; color:#2a2a4a; letter-spacing:2px;">
      BUILT WITH COFFEE + CURIOSITY · JAKARTA · ID
    </div>
  </div>

</div>

<script>
  // Stars
  const starsEl = document.getElementById('stars');
  for (let i = 0; i < 60; i++) {
    const s = document.createElement('div');
    s.className = 'star';
    s.style.cssText = `left:${Math.random()*100}%;top:${Math.random()*100}%;--d:${1+Math.random()*3}s;--delay:${Math.random()*3}s;opacity:${Math.random()}`;
    starsEl.appendChild(s);
  }

  // Marquee
  const items = ['PHP','GO','PYTHON','JAVASCRIPT','TYPESCRIPT','C','MYSQL','DOCKER','LINUX','GIT','REST API','ALGORITHMS'];
  const track = document.getElementById('marquee');
  const doubled = [...items, ...items];
  doubled.forEach(t => {
    const el = document.createElement('div');
    el.className = 'marquee-item';
    el.innerHTML = `<span>▸</span>${t}`;
    track.appendChild(el);
  });

  // Skills
  const skills = [
    { name:'PHP',        icon:'BACK',  lvl:4, c:'#b044ff' },
    { name:'Go',         icon:'BACK',  lvl:3, c:'#00f5ff' },
    { name:'Python',     icon:'BACK',  lvl:4, c:'#ffe500' },
    { name:'JavaScript', icon:'FULL',  lvl:4, c:'#ffe500' },
    { name:'TypeScript', icon:'FULL',  lvl:3, c:'#00f5ff' },
    { name:'C',          icon:'SYS',   lvl:3, c:'#ff6b2b' },
    { name:'MySQL',      icon:'DB',    lvl:4, c:'#39ff14' },
    { name:'Docker',     icon:'OPS',   lvl:2, c:'#00f5ff' },
    { name:'Git',        icon:'TOOL',  lvl:5, c:'#ff2d78' },
    { name:'Linux',      icon:'SYS',   lvl:4, c:'#ff6b2b' },
  ];
  const grid = document.getElementById('skillGrid');
  skills.forEach(sk => {
    const el = document.createElement('div');
    el.className = 'skill-card';
    el.style.setProperty('--c', sk.c);
    const pips = Array.from({length:5}, (_,i) =>
      `<div class="lvl-pip${i < sk.lvl ? ' filled' : ''}" style="--c:${sk.c}"></div>`
    ).join('');
    el.innerHTML = `<span class="skill-icon" style="color:${sk.c}">${sk.icon}</span><span class="skill-name">${sk.name}</span><div class="skill-lvl">${pips}</div>`;
    grid.appendChild(el);
  });

  // Stats
  const stats = [
    { label:'LANGUAGES',  value:'10+',  sub:'in the stack',  c:'#00f5ff', delay:'0.1s' },
    { label:'FOCUS',      value:'BACK', sub:'end leaning',   c:'#ff2d78', delay:'0.2s' },
    { label:'COMMITS',    value:'∞',    sub:'and counting',  c:'#39ff14', delay:'0.3s' },
    { label:'COFFEE/DAY', value:'3+',   sub:'cups required', c:'#ffe500', delay:'0.4s' },
  ];
  const row = document.getElementById('statsRow');
  stats.forEach(st => {
    const el = document.createElement('div');
    el.className = 'stat-box';
    el.style.setProperty('--c', st.c);
    el.innerHTML = `<span class="stat-label">${st.label}</span><span class="stat-value" style="--delay:${st.delay}">${st.value}</span><span class="stat-sub">${st.sub}</span>`;
    row.appendChild(el);
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(r => observer.observe(r));
</script>
</body>
</html>
