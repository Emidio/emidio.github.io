---
layout: default
---

<style>
  /* ── Reset & base ─────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg:        #0d1117;
    --surface:   #161b22;
    --border:    #30363d;
    --accent:    #58a6ff;
    --accent2:   #3fb950;
    --accent3:   #f78166;
    --text:      #e6edf3;
    --muted:     #8b949e;
    --radius:    10px;
    --font-mono: 'JetBrains Mono', 'Fira Code', 'Cascadia Code', monospace;
    --font-sans: 'Inter', system-ui, sans-serif;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-sans);
    line-height: 1.65;
    -webkit-font-smoothing: antialiased;
  }

  /* Cayman overrides */
  .page-header {
    background: linear-gradient(135deg, #0d1117 0%, #161b22 50%, #0d2137 100%) !important;
    border-bottom: 1px solid var(--border);
    padding: 3rem 2rem !important;
    position: relative;
    overflow: hidden;
  }
  .page-header::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 70% 50%, rgba(88,166,255,.08) 0%, transparent 70%),
      radial-gradient(ellipse 30% 50% at 20% 80%, rgba(63,185,80,.05) 0%, transparent 60%);
    pointer-events: none;
  }
  .project-name {
    font-family: var(--font-mono) !important;
    letter-spacing: -.02em !important;
    font-size: clamp(1.8rem, 4vw, 2.8rem) !important;
  }
  .project-name::before { content: '> '; color: var(--accent2); }
  .project-tagline {
    color: var(--muted) !important;
    font-family: var(--font-mono) !important;
    font-size: .95rem !important;
  }
  .btn {
    background: transparent !important;
    border: 1px solid var(--border) !important;
    color: var(--accent) !important;
    font-family: var(--font-mono) !important;
    font-size: .8rem !important;
    border-radius: var(--radius) !important;
    transition: border-color .2s, background .2s !important;
  }
  .btn:hover {
    background: rgba(88,166,255,.1) !important;
    border-color: var(--accent) !important;
  }
  .main-content { max-width: 900px !important; padding: 2rem 1.5rem !important; }
  .main-content h1, .main-content h2, .main-content h3 {
    font-family: var(--font-mono);
    color: var(--text);
    border: none !important;
  }
  .main-content a { color: var(--accent); text-decoration: none; }
  .main-content a:hover { text-decoration: underline; }

  /* ── Sections ─────────────────────────────────── */
  .er-section { margin: 2.5rem 0; }
  .er-section-title {
    font-family: var(--font-mono);
    font-size: 1rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: .12em;
    margin-bottom: 1.2rem;
    display: flex;
    align-items: center;
    gap: .6rem;
  }
  .er-section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── About card ───────────────────────────────── */
  .er-about {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.5rem;
    display: flex;
    gap: 1.5rem;
    align-items: flex-start;
  }
  .er-about-avatar {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    border: 2px solid var(--border);
    flex-shrink: 0;
  }
  .er-about-text p { color: var(--muted); font-size: .95rem; margin-bottom: .6rem; }
  .er-about-text p:last-child { margin-bottom: 0; }
  .er-badge {
    display: inline-block;
    background: rgba(88,166,255,.1);
    border: 1px solid rgba(88,166,255,.3);
    color: var(--accent);
    font-family: var(--font-mono);
    font-size: .75rem;
    border-radius: 20px;
    padding: .15rem .65rem;
    margin: .2rem .2rem 0 0;
  }
  .er-badge.green {
    background: rgba(63,185,80,.1);
    border-color: rgba(63,185,80,.3);
    color: var(--accent2);
  }

  /* ── Repo grid ────────────────────────────────── */
  .er-repos {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 1rem;
  }
  .er-repo-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.2rem;
    display: flex;
    flex-direction: column;
    gap: .5rem;
    transition: border-color .2s, transform .15s;
  }
  .er-repo-card:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }
  .er-repo-name {
    font-family: var(--font-mono);
    font-size: .95rem;
    color: var(--accent);
    font-weight: 600;
  }
  .er-repo-name::before { content: '📦 '; }
  .er-repo-desc {
    font-size: .85rem;
    color: var(--muted);
    flex: 1;
    line-height: 1.5;
  }
  .er-repo-lang {
    font-family: var(--font-mono);
    font-size: .75rem;
    color: var(--muted);
    margin-top: .3rem;
  }
  .er-repo-lang span {
    display: inline-block;
    width: 10px; height: 10px;
    border-radius: 50%;
    margin-right: .35rem;
    vertical-align: middle;
  }
  .lang-python { background: #3572a5; }
  .lang-php    { background: #4f5d95; }
  .lang-css    { background: #563d7c; }
  .lang-java   { background: #b07219; }
  .lang-other  { background: var(--muted); }

  /* ── Posts list ───────────────────────────────── */
  .er-posts { display: flex; flex-direction: column; gap: .6rem; }
  .er-post-row {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: .9rem 1.1rem;
    display: flex;
    align-items: baseline;
    gap: 1rem;
    transition: border-color .2s;
  }
  .er-post-row:hover { border-color: var(--accent); }
  .er-post-cat {
    font-family: var(--font-mono);
    font-size: .7rem;
    color: var(--muted);
    white-space: nowrap;
    min-width: 130px;
    padding: .15rem .5rem;
    border-radius: 4px;
    border: 1px solid var(--border);
    text-align: center;
  }
  .er-post-cat.cat-tech  { color: var(--accent);  border-color: rgba(88,166,255,.3);  background: rgba(88,166,255,.06); }
  .er-post-cat.cat-web   { color: var(--accent2); border-color: rgba(63,185,80,.3);   background: rgba(63,185,80,.06); }
  .er-post-cat.cat-mob   { color: #d2a8ff;        border-color: rgba(210,168,255,.3); background: rgba(210,168,255,.06); }
  .er-post-cat.cat-life  { color: var(--accent3); border-color: rgba(247,129,102,.3); background: rgba(247,129,102,.06); }
  .er-post-title { font-size: .92rem; color: var(--text); flex: 1; }
  .er-post-date {
    font-family: var(--font-mono);
    font-size: .72rem;
    color: var(--muted);
    white-space: nowrap;
  }

  /* ── Links row ────────────────────────────────── */
  .er-links {
    display: flex;
    flex-wrap: wrap;
    gap: .75rem;
    margin-top: .5rem;
  }
  .er-link-pill {
    display: inline-flex;
    align-items: center;
    gap: .4rem;
    padding: .4rem .9rem;
    border-radius: 20px;
    border: 1px solid var(--border);
    font-family: var(--font-mono);
    font-size: .8rem;
    color: var(--muted);
    text-decoration: none !important;
    transition: color .2s, border-color .2s, background .2s;
  }
  .er-link-pill:hover {
    color: var(--text) !important;
    border-color: var(--accent);
    background: rgba(88,166,255,.08);
  }

  @media (max-width: 600px) {
    .er-about { flex-direction: column; }
    .er-post-cat { min-width: unset; }
    .er-post-date { display: none; }
  }
</style>

<div class="er-section">
  <div class="er-section-title">whoami</div>
  <div class="er-about">
    <img class="er-about-avatar"
         src="https://avatars.githubusercontent.com/u/4279305?v=4"
         alt="Emidio Reggiani">
    <div class="er-about-text">
      <p>
        Hi, I'm <strong>Emidio Reggiani</strong>, a developer and tech enthusiast based in Italy.
        I tinker with servers, home automation, Android, web platforms and everything in between.
        I run a flat-file blog at <a href="https://emidio.reggiani.link">emidio.reggiani.link</a>
        powered by a <em>heavily modded</em> version of HTMLy — complete with a local comment
        system and Matomo integration that I built myself.
      </p>
      <p>
        <span class="er-badge">Python</span>
        <span class="er-badge">PHP</span>
        <span class="er-badge">Java</span>
        <span class="er-badge">CSS</span>
        <span class="er-badge green">Zabbix</span>
        <span class="er-badge green">Apache</span>
        <span class="er-badge green">Self-hosted</span>
        <span class="er-badge green">Open Source</span>
      </p>
    </div>
  </div>
</div>

---

<div class="er-section">
  <div class="er-section-title">🔗 connect</div>
  <div class="er-links">
    <a class="er-link-pill" href="https://emidio.reggiani.link">🌐 emidio.reggiani.link</a>
    <a class="er-link-pill" href="https://github.com/Emidio">🐙 github.com/Emidio</a>
    <a class="er-link-pill" href="https://it.linkedin.com/in/emidioreggiani">💼 LinkedIn</a>
    <a class="er-link-pill" href="https://www.instagram.com/pdor70/">📷 Instagram</a>
    <a class="er-link-pill" href="https://emidio.reggiani.link/feed/rss">📡 RSS Feed</a>
  </div>
</div>

---

<div class="er-section">
  <div class="er-section-title">📦 github repositories</div>
  <div class="er-repos">

    <a href="https://github.com/Emidio/htmly" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">htmly</div>
      <div class="er-repo-desc">
        Databaseless PHP blogging platform (flat-file CMS), forked from danpros/htmly and extended
        with a local comment system and Matomo analytics integration.
      </div>
      <div class="er-repo-lang"><span class="lang-php"></span>PHP · ⭐ 2</div>
    </a>

    <a href="https://github.com/Emidio/htmly-theme-ovi" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">htmly-theme-ovi</div>
      <div class="er-repo-desc">
        "Ovi" — a clean HTMLy theme derived from Occasio, reworked with round corners, improved
        banner layout and full comment system support.
      </div>
      <div class="er-repo-lang"><span class="lang-css"></span>CSS · ⭐ 1</div>
    </a>

    <a href="https://github.com/Emidio/zabbix_template_powerwall" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">zabbix_template_powerwall</div>
      <div class="er-repo-desc">
        Quick and practical Python script to pull Tesla Powerwall 2 stats directly into Zabbix
        for monitoring and historical logging.
      </div>
      <div class="er-repo-lang"><span class="lang-python"></span>Python</div>
    </a>

    <a href="https://github.com/Emidio/zabbix_template_solaredge_modbus" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">zabbix_template_solaredge_modbus</div>
      <div class="er-repo-desc">
        Import SolarEdge HDWave inverter stats into Zabbix via Modbus. Pairs perfectly with the
        Powerwall template for full solar-system monitoring.
      </div>
      <div class="er-repo-lang"><span class="lang-python"></span>Python</div>
    </a>

    <a href="https://github.com/Emidio/apple_notes_to_google_keep" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">apple_notes_to_google_keep</div>
      <div class="er-repo-desc">
        Python script to migrate notes from Apple Notes to Google Keep — handy when switching
        from iPhone to Android without losing your notes history.
      </div>
      <div class="er-repo-lang"><span class="lang-python"></span>Python</div>
    </a>

    <a href="https://github.com/Emidio/moppy-pi" class="er-repo-card" style="text-decoration:none">
      <div class="er-repo-name">moppy-pi</div>
      <div class="er-repo-desc">
        Musical controller for a Raspberry Pi floppy drive set — a fun fork of wendlers/Moppy,
        updated to work on the latest Pi images.
      </div>
      <div class="er-repo-lang"><span class="lang-java"></span>Java</div>
    </a>

  </div>
</div>

---

<div class="er-section">
  <div class="er-section-title">✍️ latest blog posts</div>
  <div class="er-posts">

    <a href="https://emidio.reggiani.link/post/maxmind-geoip-in-apache" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-tech">Tech Playground</span>
      <span class="er-post-title">MaxMind GeoIP in Apache</span>
      <span class="er-post-date">Mar 2026</span>
    </a>

    <a href="https://emidio.reggiani.link/post/matomo-integration-in-htmly" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-web">Web Development</span>
      <span class="er-post-title">Matomo integration in HTMLy</span>
      <span class="er-post-date">Mar 2026</span>
    </a>

    <a href="https://emidio.reggiani.link/post/htmly-simple-comment-system" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-web">Web Development</span>
      <span class="er-post-title">HTMLy simple comment system</span>
      <span class="er-post-date">Nov 2025</span>
    </a>

    <a href="https://emidio.reggiani.link/post/ovi-htmly-theme" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-web">Web Development</span>
      <span class="er-post-title">Ovi HTMLy Theme</span>
      <span class="er-post-date">Nov 2025</span>
    </a>

    <a href="https://emidio.reggiani.link/post/moving-to-htmly" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-mob">Android & Mobile</span>
      <span class="er-post-title">Moving to HTMLy</span>
      <span class="er-post-date">Nov 2025</span>
    </a>

    <a href="https://emidio.reggiani.link/post/apple-notes-to-google-keep" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-mob">Android & Mobile</span>
      <span class="er-post-title">Apple Notes to Google Keep</span>
      <span class="er-post-date">Dec 2024</span>
    </a>

    <a href="https://emidio.reggiani.link/post/tesla-powerwall-and-solaredge-inverter-monitoring-with-zabbix" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-tech">Tech Playground</span>
      <span class="er-post-title">Tesla Powerwall &amp; SolarEdge monitoring with Zabbix</span>
      <span class="er-post-date">Aug 2023</span>
    </a>

    <a href="https://emidio.reggiani.link/post/vmware-smtp-rule" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-tech">Tech Playground</span>
      <span class="er-post-title">VMware vSphere 5.x/6.x — Ghetto VCB &amp; SMTP firewall rule</span>
      <span class="er-post-date">May 2017</span>
    </a>

    <a href="https://emidio.reggiani.link/post/pebble-screen-tearing-fix" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-mob">Android & Mobile</span>
      <span class="er-post-title">Pebble screen tearing fix</span>
      <span class="er-post-date">Jan 2015</span>
    </a>

    <a href="https://emidio.reggiani.link/post/curl-on-phpapachewin7-64bit" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-web">Web Development</span>
      <span class="er-post-title">cURL on PHP/Apache/Win7 (64bit)</span>
      <span class="er-post-date">Jan 2012</span>
    </a>

    <a href="https://emidio.reggiani.link/post/zighini" class="er-post-row" style="text-decoration:none">
      <span class="er-post-cat cat-life">Life & Recipes</span>
      <span class="er-post-title">Zighinì — Ethiopian spiced meat recipe</span>
      <span class="er-post-date">Dec 2011</span>
    </a>

  </div>

  <p style="margin-top:1rem; font-size:.85rem; color:var(--muted)">
    → All posts on <a href="https://emidio.reggiani.link">emidio.reggiani.link</a>
  </p>
</div>
