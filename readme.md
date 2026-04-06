<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Shams — GitHub README</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet" />
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --c0: #0d1117;
      --c1: #161b22;
      --c2: #21262d;
      --c3: #30363d;
      --c4: #8b949e;
      --c5: #e6edf3;
      --accent:  #58a6ff;
      --accent2: #3fb950;
      --accent3: #ff7b72;
      --accent4: #d2a8ff;
      --mono: 'JetBrains Mono', monospace;
      --display: 'Syne', sans-serif;
    }

    body {
      background: var(--c0);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 2rem 1rem;
    }

    .readme {
      background: var(--c0);
      font-family: var(--mono);
      color: var(--c5);
      padding: 2rem 1.75rem 2.5rem;
      width: 100%;
      max-width: 720px;
      position: relative;
      overflow: hidden;
      border: 1px solid var(--c3);
      border-radius: 12px;
    }

    .grid-bg {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(var(--c1) 1px, transparent 1px),
        linear-gradient(90deg, var(--c1) 1px, transparent 1px);
      background-size: 32px 32px;
      opacity: 0.4;
      pointer-events: none;
    }

    .header {
      position: relative;
      margin-bottom: 2.5rem;
      text-align: center;
    }

    .ascii-name {
      font-family: var(--mono);
      font-size: 7px;
      line-height: 1.2;
      color: var(--accent);
      letter-spacing: 0.02em;
      white-space: pre;
      display: inline-block;
      text-shadow: 0 0 20px rgba(88,166,255,0.3);
      animation: fadeIn 0.6s ease both;
    }

    .tagline {
      font-family: var(--display);
      font-size: 11px;
      letter-spacing: 0.25em;
      color: var(--c4);
      text-transform: uppercase;
      margin-top: 0.75rem;
      animation: fadeIn 0.8s 0.2s ease both;
    }

    .badges {
      display: flex;
      justify-content: center;
      gap: 8px;
      margin-top: 1rem;
      flex-wrap: wrap;
      animation: fadeIn 0.8s 0.3s ease both;
    }

    .badge {
      background: var(--c2);
      border: 1px solid var(--c3);
      border-radius: 4px;
      padding: 3px 10px;
      font-size: 10px;
      font-family: var(--mono);
      color: var(--accent);
      letter-spacing: 0.05em;
      cursor: default;
      transition: border-color 0.2s, background 0.2s;
    }

    .badge:hover {
      border-color: var(--accent);
      background: rgba(88,166,255,0.1);
    }

    hr.divider {
      border: none;
      border-top: 1px solid var(--c3);
      margin: 1.5rem 0;
    }

    .section {
      margin-bottom: 1.75rem;
      animation: slideUp 0.5s ease both;
    }

    .cmd-line {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 0.75rem;
    }

    .prompt { color: var(--accent2); font-size: 12px; }
    .cmd    { color: var(--accent4); font-size: 12px; font-weight: 500; }

    .code-block {
      background: var(--c1);
      border: 1px solid var(--c3);
      border-radius: 8px;
      padding: 1rem 1.25rem;
      font-size: 11px;
      line-height: 1.8;
      position: relative;
      overflow: hidden;
    }

    .code-block::before {
      content: '';
      position: absolute;
      left: 0; top: 0; bottom: 0;
      width: 3px;
      background: linear-gradient(to bottom, var(--accent), var(--accent4));
      border-radius: 8px 0 0 8px;
    }

    .whoami-text {
      color: var(--c4);
      font-size: 12px;
      line-height: 1.8;
      padding: 0.5rem 0;
    }

    .whoami-text strong {
      color: var(--accent);
      font-weight: 500;
    }

    .status-row {
      display: flex;
      gap: 12px;
      align-items: flex-start;
      padding: 3px 0;
    }

    .arrow      { color: var(--accent3); font-size: 11px; min-width: 12px; }
    .status-key { color: var(--c4);      font-size: 11px; min-width: 70px; }
    .status-val { color: var(--c5);      font-size: 11px; }

    .stack-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
    }

    .stack-row { display: flex; gap: 10px; padding: 4px 0; }
    .stack-key { font-size: 10px; min-width: 70px; opacity: 0.9; }
    .stack-val { color: var(--c5); font-size: 10px; opacity: 0.85; }

    .links-row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .link-chip {
      display: flex;
      align-items: center;
      gap: 6px;
      background: var(--c2);
      border: 1px solid var(--c3);
      border-radius: 6px;
      padding: 5px 12px;
      font-size: 10px;
      color: var(--c4);
      text-decoration: none;
      transition: all 0.2s;
      cursor: pointer;
    }

    .link-chip:hover {
      border-color: var(--accent);
      color: var(--accent);
      background: rgba(88,166,255,0.08);
    }

    .link-dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      flex-shrink: 0;
    }

    .streak-container {
      background: var(--c1);
      border: 1px solid var(--c3);
      border-radius: 8px;
      padding: 1rem;
      text-align: center;
    }

    .streak-img {
      width: 100%;
      max-width: 500px;
      filter: brightness(0.9);
      border-radius: 4px;
    }

    .footer-line {
      display: flex;
      align-items: center;
      gap: 8px;
      color: var(--c4);
      font-size: 10px;
      margin-top: 1.5rem;
      padding-top: 1rem;
      border-top: 1px solid var(--c2);
    }

    .cursor {
      display: inline-block;
      width: 8px; height: 13px;
      background: var(--accent);
      animation: blink 1.1s step-end infinite;
      vertical-align: middle;
      margin-left: 2px;
      border-radius: 1px;
    }

    @keyframes blink    { 0%,100%{opacity:1} 50%{opacity:0} }
    @keyframes fadeIn   { from{opacity:0;transform:translateY(-6px)} to{opacity:1;transform:none} }
    @keyframes slideUp  { from{opacity:0;transform:translateY(10px)} to{opacity:1;transform:none} }

    .s1 { animation-delay: 0.1s }
    .s2 { animation-delay: 0.2s }
    .s3 { animation-delay: 0.3s }
    .s4 { animation-delay: 0.4s }
    .s5 { animation-delay: 0.5s }
  </style>
</head>
<body>
  <div class="readme">
    <div class="grid-bg"></div>

    <!-- Header -->
    <div class="header">
      <pre class="ascii-name">███████╗██╗  ██╗ █████╗ ███╗   ███╗███████╗
██╔════╝██║  ██║██╔══██╗████╗ ████║██╔════╝
███████╗███████║███████║██╔████╔██║███████╗
╚════██║██╔══██║██╔══██║██║╚██╔╝██║╚════██║
███████║██║  ██║██║  ██║██║ ╚═╝ ██║███████║
╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝</pre>
      <div class="tagline">CS @ UBC &nbsp;·&nbsp; AI &nbsp;·&nbsp; Full-Stack &nbsp;·&nbsp; DevOps</div>
      <div class="badges">
        <span class="badge">🎓 UBC Computer Science</span>
        <span class="badge">📍 Vancouver, BC</span>
        <span class="badge">⚡ Open to opportunities</span>
      </div>
    </div>

    <!-- whoami -->
    <div class="section s1">
      <div class="cmd-line">
        <span class="prompt">$</span>
        <span class="cmd">whoami</span>
      </div>
      <div class="code-block">
        <p class="whoami-text">
          CS student at <strong>UBC</strong> building at the intersection of <strong>AI</strong>,
          scalable backend systems, and clean developer tooling.
          Currently exploring DevOps and cloud infrastructure.
        </p>
      </div>
    </div>

    <!-- status -->
    <div class="section s2">
      <div class="cmd-line">
        <span class="prompt">$</span>
        <span class="cmd">cat status.txt</span>
      </div>
      <div class="code-block">
        <div class="status-row">
          <span class="arrow">→</span>
          <span class="status-key">building</span>
          <span class="status-val">AI-powered developer tools and full-stack applications</span>
        </div>
        <div class="status-row">
          <span class="arrow">→</span>
          <span class="status-key">learning</span>
          <span class="status-val">cloud architecture and distributed systems</span>
        </div>
        <div class="status-row">
          <span class="arrow">→</span>
          <span class="status-key">reach me</span>
          <span class="status-val" style="color: var(--accent);">shamsetabriz00@gmail.com</span>
        </div>
      </div>
    </div>

    <!-- stack -->
    <div class="section s3">
      <div class="cmd-line">
        <span class="prompt">$</span>
        <span class="cmd">cat stack.txt</span>
      </div>
      <div class="code-block">
        <div class="stack-grid">
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent);">languages</span>
            <span class="stack-val">TypeScript · JS · Python · C++ · Java</span>
          </div>
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent2);">frontend</span>
            <span class="stack-val">React · React Native · Vue · Angular</span>
          </div>
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent4);">backend</span>
            <span class="stack-val">Node.js · Express · FeathersJS</span>
          </div>
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent3);">databases</span>
            <span class="stack-val">PostgreSQL · MongoDB · MySQL · Redis</span>
          </div>
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent);">infra</span>
            <span class="stack-val">Docker · GitHub Actions · AWS</span>
          </div>
          <div class="stack-row">
            <span class="stack-key" style="color: var(--accent2);">testing</span>
            <span class="stack-val">Jest · Selenium</span>
          </div>
        </div>
      </div>
    </div>

    <!-- git log -->
    <div class="section s4">
      <div class="cmd-line">
        <span class="prompt">$</span>
        <span class="cmd">git log --oneline</span>
      </div>
      <div class="streak-container">
        <img
          class="streak-img"
          src="https://github-readme-streak-stats.herokuapp.com/?user=TeaBreeze00&hide_border=true&theme=dark&background=161b22&ring=58a6ff&fire=ff7b72&currStreakLabel=58a6ff&sideLabels=8b949e&dates=8b949e&currStreakNum=e6edf3&sideNums=e6edf3"
          alt="GitHub streak stats"
        />
      </div>
    </div>

    <!-- links -->
    <div class="section s5">
      <div class="cmd-line">
        <span class="prompt">$</span>
        <span class="cmd">cat links.txt</span>
      </div>
      <div class="links-row">
        <a class="link-chip" href="https://www.linkedin.com/in/shams-e-tibriz/">
          <span class="link-dot" style="background: #0A66C2;"></span>
          linkedin / shams-e-tibriz
        </a>
        <a class="link-chip" href="mailto:shamsetabriz00@gmail.com">
          <span class="link-dot" style="background: #EA4335;"></span>
          shamsetabriz00@gmail.com
        </a>
        <a class="link-chip" href="https://github.com/TeaBreeze00">
          <span class="link-dot" style="background: var(--accent2);"></span>
          github / TeaBreeze00
        </a>
      </div>
    </div>

    <!-- footer -->
    <div class="footer-line">
      <span style="color: var(--accent2);">✓</span>
      <span>thanks for visiting</span>
      <span class="cursor"></span>
    </div>
  </div>
</body>
</html>
