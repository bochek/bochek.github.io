<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Andrei Bochek — Technical Artist / AI Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --bg2: #111118;
    --bg3: #18181f;
    --bg4: #1e1e28;
    --text: #e8e8f0;
    --text-muted: #8888a0;
    --text-dim: #55556a;
    --cyan: #00e5ff;
    --cyan-dim: #00a8bb;
    --orange: #ff6b2c;
    --orange-dim: #cc5520;
    --border: #2a2a38;
    --card: #13131c;
    --glow-cyan: 0 0 20px rgba(0,229,255,0.15);
    --glow-orange: 0 0 20px rgba(255,107,44,0.15);
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Inter', system-ui, sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.6;
    overflow-x: hidden;
  }
  ::selection { background: var(--cyan); color: var(--bg); }
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--cyan-dim); }

  .container {
    display: grid;
    grid-template-columns: 340px 1fr;
    min-height: 100vh;
    max-width: 1400px;
    margin: 0 auto;
  }

  /* Sidebar */
  .sidebar {
    background: var(--bg2);
    border-right: 1px solid var(--border);
    padding: 48px 32px;
    position: sticky;
    top: 0;
    height: 100vh;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
  .sidebar::-webkit-scrollbar { width: 3px; }

  .avatar-block { text-align: center; }
  .avatar {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--cyan) 0%, var(--orange) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 20px;
    font-size: 42px;
    font-weight: 900;
    color: var(--bg);
    box-shadow: var(--glow-cyan), var(--glow-orange);
    position: relative;
    overflow: hidden;
  }
  .avatar::after {
    content: '';
    position: absolute;
    inset: -2px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--cyan), var(--orange));
    z-index: -1;
    animation: rotate 4s linear infinite;
  }
  @keyframes rotate { to { transform: rotate(360deg); } }

  .name-block h1 {
    font-size: 26px;
    font-weight: 800;
    letter-spacing: -0.5px;
    line-height: 1.2;
  }
  .name-block h1 .highlight-cyan { color: var(--cyan); }
  .name-block h1 .highlight-orange { color: var(--orange); }
  .title-line { font-size: 13px; color: var(--text-muted); margin-top: 6px; font-weight: 400; }

  .contact-section h3,
  .links-section h3,
  .skills-section h3 {
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: var(--text-dim);
    margin-bottom: 16px;
    font-weight: 600;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 8px 0;
    border-bottom: 1px solid var(--border);
    font-size: 13px;
  }
  .contact-item:last-child { border-bottom: none; }
  .contact-item .icon {
    width: 32px;
    height: 32px;
    border-radius: 8px;
    background: var(--bg3);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
    transition: background 0.2s, box-shadow 0.2s;
  }
  .contact-item:hover .icon { background: var(--bg4); box-shadow: var(--glow-cyan); }
  .contact-item .label { color: var(--text-dim); font-size: 11px; display: block; }
  .contact-item .value { color: var(--text); }
  .contact-item a { color: var(--text); text-decoration: none; transition: color 0.2s; }
  .contact-item a:hover { color: var(--cyan); }

  .links-section .link-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 13px;
  }
  .links-section .link-item:last-child { border-bottom: none; }
  .links-section .link-item .icon {
    width: 32px;
    height: 32px;
    border-radius: 8px;
    background: var(--bg3);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
    transition: background 0.2s;
    font-weight: 700;
  }
  .links-section .link-item:hover .icon { background: var(--cyan-dim); }
  .links-section a { color: var(--text); text-decoration: none; transition: color 0.2s; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
  .links-section a:hover { color: var(--cyan); }

  .sidebar-skill-tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 12px;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 20px;
    font-size: 12px;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
    transition: all 0.2s;
    cursor: default;
  }
  .sidebar-skill-tag:hover { border-color: var(--cyan-dim); color: var(--cyan); box-shadow: var(--glow-cyan); }
  .sidebar-skill-tag.orange:hover { border-color: var(--orange-dim); color: var(--orange); box-shadow: var(--glow-orange); }
  .skills-wrap { display: flex; flex-wrap: wrap; gap: 8px; }

  /* Main */
  .main { padding: 48px 56px; display: flex; flex-direction: column; gap: 48px; }

  .section { opacity: 0; transform: translateY(20px); transition: opacity 0.5s ease, transform 0.5s ease; }
  .section.visible { opacity: 1; transform: translateY(0); }

  .section-title {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 3px;
    color: var(--text-dim);
    font-weight: 700;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-title::after { content: ''; flex: 1; height: 1px; background: var(--border); }
  .section-title .num { color: var(--cyan); font-family: 'JetBrains Mono', monospace; font-size: 10px; }

  .profile-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px;
    position: relative;
    overflow: hidden;
  }
  .profile-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--cyan), var(--orange));
  }
  .profile-card p { font-size: 15px; line-height: 1.75; color: var(--text-muted); }
  .profile-card p strong { color: var(--text); font-weight: 600; }

  /* AI Special Section */
  .ai-hero-card {
    background: linear-gradient(135deg, #0d1a1f 0%, #1a0f08 100%);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px;
    position: relative;
    overflow: hidden;
  }
  .ai-hero-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--orange), var(--cyan));
  }
  .ai-hero-card p { font-size: 14.5px; line-height: 1.75; color: var(--text-muted); }
  .ai-hero-card p strong { color: var(--text); }
  .ai-hero-card ul { margin-top: 16px; padding-left: 0; list-style: none; }
  .ai-hero-card ul li {
    margin-bottom: 8px;
    padding-left: 18px;
    position: relative;
    font-size: 14px;
    color: var(--text-muted);
  }
  .ai-hero-card ul li::before { content: '▹'; position: absolute; left: 0; color: var(--orange); top: 1px; }
  .ai-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 4px 12px;
    background: rgba(255,107,44,0.12);
    border: 1px solid rgba(255,107,44,0.3);
    border-radius: 20px;
    font-size: 11px;
    color: var(--orange);
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 20px;
  }

  /* Experience */
  .exp-list { display: flex; flex-direction: column; gap: 24px; }
  .exp-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    position: relative;
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  .exp-item:hover { border-color: var(--cyan-dim); box-shadow: var(--glow-cyan); }
  .exp-item::before {
    content: '';
    position: absolute;
    left: 0; top: 24px; bottom: 24px;
    width: 2px;
    background: linear-gradient(180deg, var(--cyan), var(--orange));
    border-radius: 1px;
    opacity: 0;
    transition: opacity 0.3s;
  }
  .exp-item:hover::before { opacity: 1; }
  .exp-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 12px; gap: 16px; }
  .exp-title { font-size: 17px; font-weight: 700; color: var(--text); }
  .exp-company { font-size: 13px; color: var(--cyan); font-weight: 500; margin-top: 2px; }
  .exp-period { font-size: 12px; color: var(--text-dim); font-family: 'JetBrains Mono', monospace; white-space: nowrap; background: var(--bg3); padding: 4px 10px; border-radius: 6px; border: 1px solid var(--border); }
  .exp-desc { font-size: 14px; color: var(--text-muted); line-height: 1.7; }
  .exp-desc li { margin-bottom: 6px; padding-left: 16px; position: relative; list-style: none; }
  .exp-desc li::before { content: '▹'; position: absolute; left: 0; color: var(--orange); font-size: 12px; top: 2px; }

  /* Skills grid */
  .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 16px; }
  .skill-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 24px;
    transition: all 0.3s;
  }
  .skill-card:hover { border-color: var(--cyan-dim); box-shadow: var(--glow-cyan); transform: translateY(-2px); }
  .skill-card.orange-accent:hover { border-color: var(--orange-dim); box-shadow: var(--glow-orange); }
  .skill-card h4 { font-size: 14px; font-weight: 700; margin-bottom: 12px; display: flex; align-items: center; gap: 8px; }
  .skill-card h4 .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--cyan); }
  .skill-card.orange-accent h4 .dot { background: var(--orange); }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-size: 11px;
    padding: 4px 10px;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 6px;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
    transition: all 0.2s;
  }
  .tag:hover { border-color: var(--cyan-dim); color: var(--cyan); }
  .tag.orange:hover { border-color: var(--orange-dim); color: var(--orange); }

  /* Education */
  .edu-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 24px 32px;
    display: flex;
    align-items: center;
    gap: 24px;
    transition: all 0.3s;
  }
  .edu-item:hover { border-color: var(--orange-dim); box-shadow: var(--glow-orange); }
  .edu-icon { width: 52px; height: 52px; border-radius: 12px; background: var(--bg3); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-size: 22px; flex-shrink: 0; }
  .edu-info h4 { font-size: 15px; font-weight: 700; }
  .edu-info p { font-size: 13px; color: var(--text-muted); margin-top: 4px; }

  /* Languages */
  .lang-list { display: flex; gap: 16px; flex-wrap: wrap; }
  .lang-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 24px;
    display: flex;
    align-items: center;
    gap: 16px;
    transition: all 0.3s;
    flex: 1;
    min-width: 160px;
  }
  .lang-item:hover { border-color: var(--cyan-dim); box-shadow: var(--glow-cyan); }
  .lang-flag { font-size: 24px; }
  .lang-name { font-size: 14px; font-weight: 600; }
  .lang-level { font-size: 12px; color: var(--text-dim); margin-top: 2px; }

  /* Reel */
  .reel-card {
    background: linear-gradient(135deg, var(--bg3) 0%, var(--bg4) 100%);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px;
    display: flex;
    align-items: center;
    gap: 24px;
    text-decoration: none;
    color: inherit;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .reel-card::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(0,229,255,0.05), rgba(255,107,44,0.05)); opacity: 0; transition: opacity 0.3s; }
  .reel-card:hover::before { opacity: 1; }
  .reel-card:hover { border-color: var(--orange-dim); box-shadow: var(--glow-orange); transform: translateY(-2px); }
  .reel-play { width: 56px; height: 56px; border-radius: 50%; background: var(--orange); display: flex; align-items: center; justify-content: center; font-size: 20px; color: white; flex-shrink: 0; box-shadow: var(--glow-orange); transition: transform 0.2s; }
  .reel-card:hover .reel-play { transform: scale(1.1); }
  .reel-text h4 { font-size: 16px; font-weight: 700; margin-bottom: 4px; }
  .reel-text p { font-size: 13px; color: var(--text-muted); }

  /* Soft skills */
  .soft-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 12px; }
  .soft-item { background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 14px 18px; font-size: 13px; display: flex; align-items: center; gap: 10px; transition: all 0.2s; }
  .soft-item:hover { border-color: var(--cyan-dim); color: var(--cyan); }
  .soft-item .check { color: var(--cyan); font-size: 14px; }

  /* Responsive */
  @media (max-width: 900px) {
    .container { grid-template-columns: 1fr; }
    .sidebar { position: relative; height: auto; border-right: none; border-bottom: 1px solid var(--border); }
    .main { padding: 32px 24px; }
  }
  @media print {
    .sidebar { position: relative; height: auto; }
    .container { grid-template-columns: 1fr; }
    body { background: white; color: black; }
    .exp-item, .skill-card, .edu-item, .lang-item, .profile-card { break-inside: avoid; }
  }
</style>
</head>
<body>

<div class="container">

  <!-- Sidebar -->
  <aside class="sidebar">

    <div class="avatar-block">
      <div class="avatar">AB</div>
      <div class="name-block">
        <h1><span class="highlight-cyan">Andrei</span> <span class="highlight-orange">Bochek</span></h1>
        <div class="title-line">Technical Artist / AI Engineer / 3D Generalist</div>
      </div>
    </div>

    <div class="contact-section">
      <h3>Contact</h3>
      <div class="contact-item">
        <div class="icon">✦</div>
        <div>
          <span class="label">Telegram</span>
          <a href="https://t.me/bochek" target="_blank" class="value">@bochek</a>
        </div>
      </div>
      <div class="contact-item">
        <div class="icon">✈</div>
        <div>
          <span class="label">WhatsApp</span>
          <a href="https://wa.me/66812684841" target="_blank" class="value">+66 81 268-48-41</a>
        </div>
      </div>
      <div class="contact-item">
        <div class="icon">✉</div>
        <div>
          <span class="label">Email</span>
          <a href="mailto:bochektv@gmail.com" class="value">bochektv@gmail.com</a>
        </div>
      </div>
      <div class="contact-item">
        <div class="icon">⌂</div>
        <div>
          <span class="label">Location</span>
          <span class="value">Da Nang, Vietnam (remote-friendly)</span>
        </div>
      </div>
    </div>

    <div class="links-section">
      <h3>Links</h3>
      <div class="link-item">
        <div class="icon">◈</div>
        <a href="https://www.behance.net/bochek" target="_blank">behance.net/bochek</a>
      </div>
      <div class="link-item">
        <div class="icon">◎</div>
        <a href="https://zoomazooma.tilda.ws/" target="_blank">zoomazooma.tilda.ws</a>
      </div>
      <div class="link-item">
        <div class="icon">▶</div>
        <a href="https://youtu.be/pGl0x8IQ0jE" target="_blank">CG Artist Reel</a>
      </div>
      <div class="link-item">
        <div class="icon">★</div>
        <a href="https://youtu.be/F5MBwxN3hPk" target="_blank">Featured Work</a>
      </div>
      <div class="link-item">
        <div class="icon">in</div>
        <a href="https://www.linkedin.com/in/andrew-bochek-cg/" target="_blank">linkedin.com/in/andrew-bochek-cg</a>
      </div>
      <div class="link-item">
        <div class="icon">f</div>
        <a href="https://www.facebook.com/profile.php?id=100005341546456" target="_blank">facebook</a>
      </div>
      <div class="link-item">
        <div class="icon">⌥</div>
        <a href="https://github.com/bochek" target="_blank">github.com/bochek</a>
      </div>
    </div>

    <div class="skills-section">
      <h3>Core Stack</h3>
      <div class="skills-wrap">
        <span class="sidebar-skill-tag">Unreal Engine 5</span>
        <span class="sidebar-skill-tag orange">Niagara VFX</span>
        <span class="sidebar-skill-tag">Blueprint</span>
        <span class="sidebar-skill-tag orange">MetaHuman</span>
        <span class="sidebar-skill-tag">Blender</span>
        <span class="sidebar-skill-tag orange">Cinema 4D</span>
        <span class="sidebar-skill-tag">Substance</span>
        <span class="sidebar-skill-tag">After Effects</span>
        <span class="sidebar-skill-tag orange">Custom AI Agents</span>
        <span class="sidebar-skill-tag">n8n</span>
        <span class="sidebar-skill-tag orange">STT→LLM→TTS</span>
        <span class="sidebar-skill-tag">Docker</span>
        <span class="sidebar-skill-tag orange">AWS / Render</span>
        <span class="sidebar-skill-tag">C++</span>
        <span class="sidebar-skill-tag orange">C#</span>
        <span class="sidebar-skill-tag">JavaScript</span>
      </div>
    </div>

  </aside>

  <!-- Main -->
  <main class="main">

    <!-- Profile -->
    <section class="section" id="profile">
      <div class="section-title"><span class="num">01</span> Profile</div>
      <div class="profile-card">
        <p>
          Highly skilled <strong>Technical Artist</strong> and <strong>AI Engineer</strong> with years of experience creating immersive shows, VR projects, and multimedia content. I specialize in <strong>Unreal Engine</strong>, combining deep knowledge of CG/VFX pipelines with cutting-edge <strong>AI agent architectures</strong> to optimize workflows and achieve outstanding visual quality. My expertise spans concept development, previsualization, motion design, 3D asset and level creation, and integrating AI tools — from LLM-powered bots to real-time voice systems — into production pipelines. Fluent in English (Upper Intermediate).
        </p>
      </div>
    </section>

    <!-- AI Engineering — dedicated block -->
    <section class="section" id="ai-engineering">
      <div class="section-title"><span class="num">02</span> AI Engineering</div>
      <div class="ai-hero-card">
        <div class="ai-badge">⚡ 1.5+ Years Production Experience</div>
        <p>
          Over the last 1.5 years I've been building <strong>production-grade AI systems</strong> that bridge creative workflows and intelligent automation. Starting from n8n automations, I moved toward <strong>custom agent architectures</strong> designed for CG and real-time rendering environments:
        </p>
        <ul>
          <li><strong>Custom AI agents & orchestration</strong> — multi-step pipelines with memory, tool use, and decision routing for CG production tasks</li>
          <li><strong>Real-time voice pipelines (STT→LLM→TTS)</strong> — sub-second latency systems for interactive digital humans, MetaHumans with live LLM responses, and avatar applications</li>
          <li><strong>AI-driven digital asset pipelines</strong> — generative workflows for textures, references, and 3D prep using diffusion models and LLMs integrated into Unreal Engine via MetaHuman and MetaSound</li>
          <li><strong>AI-powered project management bots</strong> — LLM-backed assistants for task decomposition, deadline tracking, and client communication</li>
          <li><strong>Cloud deployment</strong> — containerized AI services on Render.com and AWS (EC2, S3, Docker); managing low-latency APIs and webhook orchestration</li>
        </ul>
      </div>
    </section>

    <!-- Experience -->
    <section class="section" id="experience">
      <div class="section-title"><span class="num">03</span> Experience</div>
      <div class="exp-list">

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">AI Engineer, Technical Artist</div>
              <div class="exp-company">Freelance — Bangkok, Thailand</div>
            </div>
            <div class="exp-period">2024 – Present</div>
          </div>
          <ul class="exp-desc">
            <li>Designed and deployed custom AI agent orchestrations for CG and real-time pipelines</li>
            <li>Built low-latency STT→LLM→TTS pipelines (sub-second voice interaction) for digital human and MetaHuman integrations</li>
            <li>Developed AI-powered project management bots with LLM-backed task decomposition and tracking</li>
            <li>Automated CG workflows using n8n: asset versioning, render farm triggers, notification routing</li>
            <li>Deployed AI services and webhooks on Render.com and AWS (EC2, Docker containers)</li>
            <li>Integrated LLM capabilities into Unreal Engine environments via MetaHuman and MetaSound</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">UE5 Generalist, Technical Artist</div>
              <div class="exp-company">EGOeast Productions (Tel Aviv) &amp; Freelance</div>
            </div>
            <div class="exp-period">2021 – Present</div>
          </div>
          <ul class="exp-desc">
            <li>Launched large-scale immersive shows with projection mapping and Christie Pandoras Box professional projection systems</li>
            <li>Developed concept art, previs, motion design; supervised projection shows (up to 30K resolution renders)</li>
            <li>Scriptwrote and produced animated VR films for children</li>
            <li>Built pipelines for 3D scanning and DeepMotion AI motion capture</li>
            <li>Created levels, lighting, and VFX in Unreal Engine 5</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">Motion Designer, CG Generalist</div>
              <div class="exp-company">Filin.pro — Moscow</div>
            </div>
            <div class="exp-period">2022 – 2023</div>
          </div>
          <ul class="exp-desc">
            <li>Created multimedia content for interactive digital installations and AR applications (exhibitions, museums, art spaces)</li>
            <li>Managed teams of freelancers and external contractors</li>
            <li>On-site technical supervision during launch of multimedia setups</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">Freelance CG Supervisor</div>
              <div class="exp-company">Radugadesign — International Projects</div>
            </div>
            <div class="exp-period">2021 – 2025</div>
          </div>
          <ul class="exp-desc">
            <li>CG supervision on major international projects: Rosatom conference, Nissan Arya launch, Oppo</li>
            <li>3D graphics and motion design for advertising campaigns</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">Supervisor of VR Post Production</div>
              <div class="exp-company">Planetpics — Digital Publishing (VR Documentaries)</div>
            </div>
            <div class="exp-period">2019 – 2021</div>
          </div>
          <ul class="exp-desc">
            <li>Built and implemented pipeline for ultra-high-resolution 360° video (8K–20K)</li>
            <li>R&D in VR applications (Unity / Unreal / Cinema 4D)</li>
            <li>Developed motion designs supporting the studio's visual style</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">Head of Video Production &amp; Editing Department</div>
              <div class="exp-company">Regional TV Companies</div>
            </div>
            <div class="exp-period">– 2008</div>
          </div>
          <ul class="exp-desc">
            <li>Led video production and post-production teams at regional television stations</li>
            <li>Developed and oversaw editorial standards, format design, and broadcast workflows</li>
            <li>Hiring, training, and managing video editors and production staff</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-header">
            <div>
              <div class="exp-title">Motion Designer / Video Editor</div>
              <div class="exp-company">Armrocks Studio, MargInfoMult, Freelance</div>
            </div>
            <div class="exp-period">2008 – 2019</div>
          </div>
          <ul class="exp-desc">
            <li>Developed graphic style and animation for documentaries and corporate films</li>
            <li>Co-founded studio, managed CG pipelines and teams</li>
            <li>TV advertising, 3D visualization, 2D/3D animation</li>
          </ul>
        </div>

      </div>
    </section>

    <!-- Skills -->
    <section class="section" id="skills">
      <div class="section-title"><span class="num">04</span> Skills & Tools</div>
      <div class="skills-grid">

        <div class="skill-card">
          <h4><span class="dot"></span> Unreal Engine</h4>
          <div class="skill-tags">
            <span class="tag">Blueprint</span>
            <span class="tag">Niagara VFX</span>
            <span class="tag">Material Editor</span>
            <span class="tag">Sequencer</span>
            <span class="tag">MetaHuman</span>
            <span class="tag">MetaSound</span>
            <span class="tag">DMX</span>
            <span class="tag">Perforce</span>
            <span class="tag">High-Res Rendering (up to 30K)</span>
            <span class="tag">Projection Mapping</span>
            <span class="tag">Christie Pandoras Box</span>
          </div>
        </div>

        <div class="skill-card orange-accent">
          <h4><span class="dot"></span> AI Engineering</h4>
          <div class="skill-tags">
            <span class="tag orange">Custom AI Agents</span>
            <span class="tag orange">Agent Orchestration</span>
            <span class="tag orange">STT→LLM→TTS Pipelines</span>
            <span class="tag orange">LLM API Integration</span>
            <span class="tag orange">Local LLM Inference</span>
            <span class="tag orange">n8n Automation</span>
            <span class="tag orange">Weavy.ai</span>
            <span class="tag orange">ComfyUI</span>
            <span class="tag orange">MetaHuman + LLM</span>
          </div>
        </div>

        <div class="skill-card">
          <h4><span class="dot"></span> 3D & Modeling</h4>
          <div class="skill-tags">
            <span class="tag">Blender</span>
            <span class="tag">Cinema 4D</span>
            <span class="tag">3ds Max</span>
            <span class="tag">Houdini</span>
            <span class="tag">Substance Painter</span>
            <span class="tag">Substance Designer</span>
            <span class="tag">Photoshop</span>
            <span class="tag">Illustrator</span>
            <span class="tag">PBR Texturing</span>
            <span class="tag">UV Mapping</span>
          </div>
        </div>

        <div class="skill-card">
          <h4><span class="dot"></span> Programming</h4>
          <div class="skill-tags">
            <span class="tag">C++</span>
            <span class="tag">C#</span>
            <span class="tag">JavaScript</span>
            <span class="tag">Python</span>
            <span class="tag">MS Visual Studio</span>
          </div>
        </div>

        <div class="skill-card orange-accent">
          <h4><span class="dot"></span> Infrastructure & DevOps</h4>
          <div class="skill-tags">
            <span class="tag orange">Docker</span>
            <span class="tag orange">WSL / Linux</span>
            <span class="tag orange">Render.com</span>
            <span class="tag orange">AWS (EC2, S3)</span>
            <span class="tag orange">Cloud App Deployment</span>
          </div>
        </div>

        <div class="skill-card orange-accent">
          <h4><span class="dot"></span> Compositing & VFX</h4>
          <div class="skill-tags">
            <span class="tag orange">After Effects</span>
            <span class="tag orange">DaVinci Fusion</span>
            <span class="tag orange">Nuke</span>
            <span class="tag orange">Premiere Pro</span>
            <span class="tag orange">DaVinci Resolve</span>
          </div>
        </div>

        <div class="skill-card">
          <h4><span class="dot"></span> Rendering</h4>
          <div class="skill-tags">
            <span class="tag">Redshift</span>
            <span class="tag">V-Ray</span>
            <span class="tag">Octane</span>
            <span class="tag">U-Render</span>
          </div>
        </div>

        <div class="skill-card orange-accent">
          <h4><span class="dot"></span> VR & Immersive</h4>
          <div class="skill-tags">
            <span class="tag orange">Oculus Quest</span>
            <span class="tag orange">360° Video</span>
            <span class="tag orange">Unity3D</span>
            <span class="tag orange">Unreal VR</span>
            <span class="tag orange">Virtual Production</span>
          </div>
        </div>

      </div>
    </section>

    <!-- Soft Skills -->
    <section class="section" id="soft">
      <div class="section-title"><span class="num">05</span> Soft Skills</div>
      <div class="soft-grid">
        <div class="soft-item"><span class="check">✓</span> Creative problem solving</div>
        <div class="soft-item"><span class="check">✓</span> Team leadership & mentorship</div>
        <div class="soft-item"><span class="check">✓</span> Deadline management</div>
        <div class="soft-item"><span class="check">✓</span> Cross-functional collaboration</div>
        <div class="soft-item"><span class="check">✓</span> Rapid tech adaptation</div>
        <div class="soft-item"><span class="check">✓</span> Distributed team experience</div>
        <div class="soft-item"><span class="check">✓</span> Technical documentation</div>
        <div class="soft-item"><span class="check">✓</span> Attention to detail</div>
      </div>
    </section>

    <!-- Education -->
    <section class="section" id="education">
      <div class="section-title"><span class="num">06</span> Education</div>
      <div class="edu-item">
        <div class="edu-icon">∑</div>
        <div class="edu-info">
          <h4>Applied Mathematics & OS Programming</h4>
          <p>Vyatka State Pedagogical University — 3.5 years</p>
        </div>
      </div>
    </section>

    <!-- Languages -->
    <section class="section" id="languages">
      <div class="section-title"><span class="num">07</span> Languages</div>
      <div class="lang-list">
        <div class="lang-item">
          <span class="lang-flag">🇷🇺</span>
          <div>
            <div class="lang-name">Russian</div>
            <div class="lang-level">Native</div>
          </div>
        </div>
        <div class="lang-item">
          <span class="lang-flag">🇬🇧</span>
          <div>
            <div class="lang-name">English</div>
            <div class="lang-level">Upper Intermediate</div>
          </div>
        </div>
        <div class="lang-item">
          <span class="lang-flag">🇹🇭</span>
          <div>
            <div class="lang-name">Thai</div>
            <div class="lang-level">Learning</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Reel CTA -->
    <section class="section" id="reel">
      <a href="https://youtu.be/pGl0x8IQ0jE" target="_blank" class="reel-card">
        <div class="reel-play">▶</div>
        <div class="reel-text">
          <h4>Watch CG Artist Reel 2024</h4>
          <p>Unreal Engine environments, VFX, motion design, VR experiences</p>
        </div>
      </a>
    </section>

    <!-- Beyond Work -->
    <section class="section" id="beyond">
      <div class="section-title"><span class="num">08</span> Beyond Work</div>
      <div class="edu-item" style="gap:20px;">
        <div class="edu-icon">🏍</div>
        <div class="edu-info">
          <h4>Motorcycle Expeditions</h4>
          <p>Long-distance motorcycle travel — planning routes through Southeast Asia, analyzing terrain, weather patterns, logistics. The same analytical mindset I bring to tech projects.</p>
        </div>
      </div>
      <div class="edu-item" style="margin-top:12px; gap:20px;">
        <div class="edu-icon">⚙</div>
        <div class="edu-info">
          <h4>Cutting-Edge Tech Experiments</h4>
          <p>Constantly launching side projects at the frontier of what's possible — diving deep into new frameworks, researching novel architectures, breaking things to understand how they really work. If it requires serious analysis and synthesising lots of new information, I'm in.</p>
        </div>
      </div>
    </section>

  </main>
</div>

<script>
  const sections = document.querySelectorAll('.section');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) entry.target.classList.add('visible');
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
  sections.forEach(s => observer.observe(s));
  setTimeout(() => sections[0]?.classList.add('visible'), 200);
</script>

</body>
</html>
