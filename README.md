<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Aivora — Web Design for Local Businesses</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Syne:wght@700;800&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
 
    :root {
      --bg: #0A0A0F;
      --surface: #13131A;
      --card: #1A1A24;
      --border: #2A2A38;
      --accent: #6C63FF;
      --accent2: #A78BFA;
      --text: #F0F0F8;
      --muted: #8888AA;
      --green: #34D399;
      --radius: 14px;
    }
 
    html { scroll-behavior: smooth; }
 
    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      font-size: 16px;
      line-height: 1.6;
      overflow-x: hidden;
    }
 
    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; justify-content: space-between; align-items: center;
      padding: 18px 5%;
      background: rgba(10,10,15,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-size: 1.2rem;
      font-weight: 800;
      color: var(--text);
      text-decoration: none;
      letter-spacing: -0.5px;
    }
    .nav-links { display: flex; gap: 32px; list-style: none; }
    .nav-links a {
      color: var(--muted); text-decoration: none;
      font-size: 0.9rem; font-weight: 500;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--text); }
    .nav-cta {
      background: var(--accent); color: #fff;
      border: none; border-radius: 8px;
      padding: 10px 22px; font-size: 0.9rem;
      font-weight: 600; cursor: pointer;
      text-decoration: none;
      transition: background 0.2s, transform 0.15s;
    }
    .nav-cta:hover { background: var(--accent2); transform: translateY(-1px); }
 
    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column;
      justify-content: center; align-items: center;
      text-align: center;
      padding: 120px 5% 80px;
      position: relative;
      overflow: hidden;
    }
    .hero-glow {
      position: absolute;
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(108,99,255,0.18) 0%, transparent 70%);
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      pointer-events: none;
    }
    .hero-badge {
      display: inline-flex; align-items: center; gap: 8px;
      background: rgba(108,99,255,0.12);
      border: 1px solid rgba(108,99,255,0.3);
      border-radius: 999px;
      padding: 6px 16px;
      font-size: 0.82rem; font-weight: 600;
      color: var(--accent2);
      margin-bottom: 28px;
      letter-spacing: 0.5px;
    }
    .hero-badge span { width: 7px; height: 7px; border-radius: 50%; background: var(--green); display: inline-block; animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.4;} }
 
    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2.6rem, 6vw, 4.8rem);
      font-weight: 800;
      line-height: 1.08;
      letter-spacing: -2px;
      margin-bottom: 24px;
      max-width: 800px;
    }
    h1 .highlight {
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .hero-sub {
      font-size: 1.15rem; color: var(--muted);
      max-width: 520px; margin-bottom: 40px;
      font-weight: 400; line-height: 1.7;
    }
    .hero-btns { display: flex; gap: 14px; flex-wrap: wrap; justify-content: center; }
    .btn-primary {
      background: var(--accent); color: #fff;
      border: none; border-radius: 10px;
      padding: 15px 32px; font-size: 1rem;
      font-weight: 600; cursor: pointer;
      text-decoration: none;
      transition: background 0.2s, transform 0.15s, box-shadow 0.2s;
      box-shadow: 0 4px 24px rgba(108,99,255,0.35);
    }
    .btn-primary:hover { background: var(--accent2); transform: translateY(-2px); box-shadow: 0 8px 32px rgba(108,99,255,0.45); }
    .btn-secondary {
      background: transparent; color: var(--text);
      border: 1px solid var(--border); border-radius: 10px;
      padding: 15px 32px; font-size: 1rem;
      font-weight: 500; cursor: pointer;
      text-decoration: none;
      transition: border-color 0.2s, transform 0.15s;
    }
    .btn-secondary:hover { border-color: var(--accent); transform: translateY(-2px); }
 
    .hero-stats {
      display: flex; gap: 48px; margin-top: 64px;
      flex-wrap: wrap; justify-content: center;
    }
    .stat { text-align: center; }
    .stat-num { font-family: 'Syne', sans-serif; font-size: 2rem; font-weight: 800; color: var(--text); }
    .stat-label { font-size: 0.82rem; color: var(--muted); margin-top: 2px; }
 
    /* SECTIONS */
    section { padding: 100px 5%; }
    .section-label {
      font-size: 0.78rem; font-weight: 700; letter-spacing: 2.5px;
      color: var(--accent); text-transform: uppercase; margin-bottom: 14px;
    }
    h2 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.8rem, 4vw, 2.8rem);
      font-weight: 800; letter-spacing: -1px;
      margin-bottom: 16px; line-height: 1.15;
    }
    .section-sub { color: var(--muted); font-size: 1.05rem; max-width: 520px; line-height: 1.7; }
    .section-header { margin-bottom: 56px; }
 
    /* WORK */
    #work { background: var(--surface); }
    .work-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 24px;
    }
    .work-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      overflow: hidden;
      transition: transform 0.25s, box-shadow 0.25s, border-color 0.25s;
      cursor: pointer;
    }
    .work-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 16px 48px rgba(0,0,0,0.4);
      border-color: var(--accent);
    }
    .work-thumb {
      height: 200px;
      display: flex; align-items: center; justify-content: center;
      font-size: 3rem; position: relative; overflow: hidden;
    }
    .thumb-1 { background: linear-gradient(135deg, #1a0a2e, #2d1b69); }
    .thumb-2 { background: linear-gradient(135deg, #0a2e1a, #1b6940); }
    .thumb-3 { background: linear-gradient(135deg, #2e1a0a, #693d1b); }
    .thumb-4 { background: linear-gradient(135deg, #0a1a2e, #1b4069); }
    .thumb-5 { background: linear-gradient(135deg, #2e0a1a, #691b40); }
    .work-mock {
      width: 80%; height: 130px;
      background: rgba(255,255,255,0.06);
      border-radius: 8px;
      border: 1px solid rgba(255,255,255,0.1);
      display: flex; flex-direction: column;
      padding: 12px; gap: 8px;
    }
    .mock-bar { height: 8px; border-radius: 4px; background: rgba(255,255,255,0.15); }
    .mock-bar.short { width: 40%; }
    .mock-bar.med { width: 65%; }
    .mock-bar.full { width: 90%; }
    .mock-bar.accent { background: var(--accent); opacity: 0.6; width: 30%; }
    .work-info { padding: 20px; }
    .work-tag {
      display: inline-block;
      background: rgba(108,99,255,0.12);
      color: var(--accent2); font-size: 0.75rem;
      font-weight: 600; border-radius: 6px;
      padding: 3px 10px; margin-bottom: 10px;
    }
    .work-title { font-weight: 700; font-size: 1.05rem; margin-bottom: 6px; }
    .work-desc { color: var(--muted); font-size: 0.88rem; line-height: 1.6; }
 
    /* SERVICES */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 20px;
    }
    .service-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 32px;
      transition: border-color 0.25s, transform 0.2s;
    }
    .service-card:hover { border-color: var(--accent); transform: translateY(-4px); }
    .service-icon {
      width: 48px; height: 48px;
      background: rgba(108,99,255,0.12);
      border-radius: 12px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem; margin-bottom: 20px;
    }
    .service-title { font-weight: 700; font-size: 1.05rem; margin-bottom: 10px; }
    .service-desc { color: var(--muted); font-size: 0.9rem; line-height: 1.65; margin-bottom: 20px; }
    .service-price {
      font-family: 'Syne', sans-serif;
      font-size: 1.5rem; font-weight: 800;
      color: var(--accent2);
    }
    .service-price span { font-size: 0.85rem; color: var(--muted); font-family: 'Inter', sans-serif; font-weight: 400; }
 
    /* ABOUT */
    #about { background: var(--surface); }
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 64px; align-items: center;
    }
    .about-visual {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 40px;
      display: flex; flex-direction: column; gap: 16px;
    }
    .skill-row { display: flex; flex-direction: column; gap: 6px; }
    .skill-label { font-size: 0.85rem; font-weight: 600; display: flex; justify-content: space-between; }
    .skill-bar { height: 6px; background: var(--border); border-radius: 3px; overflow: hidden; }
    .skill-fill {
      height: 100%; border-radius: 3px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      width: 0;
      transition: width 1.2s cubic-bezier(0.25,0.46,0.45,0.94);
    }
    .about-text p { color: var(--muted); line-height: 1.8; margin-bottom: 16px; font-size: 1rem; }
    .about-text p strong { color: var(--text); }
    .tools-list { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 24px; }
    .tool-chip {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 8px; padding: 6px 14px;
      font-size: 0.82rem; font-weight: 500; color: var(--muted);
    }
 
    /* CONTACT */
    .contact-wrapper {
      max-width: 600px; margin: 0 auto; text-align: center;
    }
    .contact-form { display: flex; flex-direction: column; gap: 16px; margin-top: 40px; text-align: left; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
    .form-group { display: flex; flex-direction: column; gap: 8px; }
    label { font-size: 0.85rem; font-weight: 600; color: var(--muted); }
    input, textarea, select {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 14px 16px;
      color: var(--text);
      font-family: 'Inter', sans-serif;
      font-size: 0.95rem;
      outline: none;
      transition: border-color 0.2s;
      width: 100%;
    }
    input:focus, textarea:focus, select:focus { border-color: var(--accent); }
    textarea { resize: vertical; min-height: 120px; }
    .submit-btn {
      background: var(--accent); color: #fff;
      border: none; border-radius: 10px;
      padding: 16px; font-size: 1rem;
      font-weight: 700; cursor: pointer;
      width: 100%;
      transition: background 0.2s, transform 0.15s;
    }
    .submit-btn:hover { background: var(--accent2); transform: translateY(-2px); }
    .form-success {
      display: none;
      background: rgba(52,211,153,0.1);
      border: 1px solid rgba(52,211,153,0.3);
      border-radius: 10px; padding: 20px;
      text-align: center; color: var(--green);
      font-weight: 600; margin-top: 16px;
    }
 
    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 32px 5%;
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 16px;
      color: var(--muted); font-size: 0.85rem;
    }
    footer a { color: var(--muted); text-decoration: none; }
    footer a:hover { color: var(--text); }
 
    /* FADE IN */
    .fade-in { opacity: 0; transform: translateY(24px); transition: opacity 0.6s ease, transform 0.6s ease; }
    .fade-in.visible { opacity: 1; transform: translateY(0); }
 
    /* MOBILE */
    @media (max-width: 768px) {
      nav .nav-links { display: none; }
      .about-grid { grid-template-columns: 1fr; }
      .form-row { grid-template-columns: 1fr; }
      .hero-stats { gap: 32px; }
    }
  </style>
</head>
<body>
 
<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Aivora</a>
  <ul class="nav-links">
    <li><a href="#work">Work</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Get a Free Quote</a>
</nav>
 
<!-- HERO -->
<section class="hero">
  <div class="hero-glow"></div>
  <div class="hero-badge"><span></span> Available for new clients — Toronto, ON</div>
  <h1>Fast, professional websites for <span class="highlight">local businesses</span></h1>
  <p class="hero-sub">I help small businesses get online quickly and affordably — using the latest AI tools to deliver a great-looking website in days, not weeks.</p>
  <div class="hero-btns">
    <a href="#work" class="btn-primary">See My Work</a>
    <a href="#contact" class="btn-secondary">Get a Free Quote</a>
  </div>
  <div class="hero-stats">
    <div class="stat"><div class="stat-num">5+</div><div class="stat-label">Sites Built</div></div>
    <div class="stat"><div class="stat-num">3</div><div class="stat-label">Days Average Delivery</div></div>
    <div class="stat"><div class="stat-num">$400</div><div class="stat-label">Starting Price</div></div>
  </div>
</section>
 
<!-- WORK -->
<section id="work">
  <div class="section-header fade-in">
    <div class="section-label">Portfolio</div>
    <h2>Recent work</h2>
    <p class="section-sub">A selection of websites built for local businesses using AI-powered tools.</p>
  </div>
  <div class="work-grid">
    <div class="work-card fade-in" onclick="openPreview('mikes')">
      <div class="work-thumb thumb-1">
        <div class="work-mock">
          <div class="mock-bar short accent"></div>
          <div class="mock-bar med"></div>
          <div class="mock-bar full"></div>
          <div class="mock-bar short"></div>
        </div>
      </div>
      <div class="work-info">
        <div class="work-tag">Barbershop</div>
        <div class="work-title">Mike's Barbershop</div>
        <div class="work-desc">Modern booking site with services, gallery, and contact form. Built in 2 days.</div>
        <div style="margin-top:12px;font-size:0.82rem;color:var(--accent);font-weight:600;">👁 Click to preview →</div>
      </div>
    </div>
    <div class="work-card fade-in" onclick="openPreview('sunrise')">
      <div class="work-thumb thumb-2">
        <div class="work-mock">
          <div class="mock-bar short accent"></div>
          <div class="mock-bar full"></div>
          <div class="mock-bar med"></div>
          <div class="mock-bar short"></div>
        </div>
      </div>
      <div class="work-info">
        <div class="work-tag">Cleaning Service</div>
        <div class="work-title">Sunrise Cleaning Co.</div>
        <div class="work-desc">Clean, trustworthy landing page with pricing and an online quote request form.</div>
        <div style="margin-top:12px;font-size:0.82rem;color:var(--accent);font-weight:600;">👁 Click to preview →</div>
      </div>
    </div>
    <div class="work-card fade-in" onclick="openPreview('bella')">
      <div class="work-thumb thumb-3">
        <div class="work-mock">
          <div class="mock-bar short accent"></div>
          <div class="mock-bar med"></div>
          <div class="mock-bar full"></div>
          <div class="mock-bar med"></div>
        </div>
      </div>
      <div class="work-info">
        <div class="work-tag">Nail Salon</div>
        <div class="work-title">Bella Nails & Spa</div>
        <div class="work-desc">Elegant portfolio site showcasing services, photo gallery, and easy booking.</div>
        <div style="margin-top:12px;font-size:0.82rem;color:var(--accent);font-weight:600;">👁 Click to preview →</div>
      </div>
    </div>
    <div class="work-card fade-in" onclick="openPreview('cafe')">
      <div class="work-thumb thumb-4">
        <div class="work-mock">
          <div class="mock-bar short accent"></div>
          <div class="mock-bar full"></div>
          <div class="mock-bar short"></div>
          <div class="mock-bar med"></div>
        </div>
      </div>
      <div class="work-info">
        <div class="work-tag">Restaurant</div>
        <div class="work-title">Café Maison</div>
        <div class="work-desc">Warm, inviting site with menu, hours, location map, and reservation link.</div>
        <div style="margin-top:12px;font-size:0.82rem;color:var(--accent);font-weight:600;">👁 Click to preview →</div>
      </div>
    </div>
    <div class="work-card fade-in" onclick="openPreview('peak')">
      <div class="work-thumb thumb-5">
        <div class="work-mock">
          <div class="mock-bar short accent"></div>
          <div class="mock-bar med"></div>
          <div class="mock-bar full"></div>
          <div class="mock-bar short"></div>
        </div>
      </div>
      <div class="work-info">
        <div class="work-tag">Contractor</div>
        <div class="work-title">Peak Renovations</div>
        <div class="work-desc">Professional trades site with before/after photos, services, and a free quote form.</div>
        <div style="margin-top:12px;font-size:0.82rem;color:var(--accent);font-weight:600;">👁 Click to preview →</div>
      </div>
    </div>
  </div>
</section>
 
<!-- PREVIEW MODAL -->
<div id="previewModal" style="display:none;position:fixed;inset:0;z-index:999;background:rgba(0,0,0,0.85);backdrop-filter:blur(6px);align-items:center;justify-content:center;padding:20px;">
  <div style="background:#0A0A0F;border:1px solid #2A2A38;border-radius:16px;width:100%;max-width:960px;height:90vh;display:flex;flex-direction:column;overflow:hidden;box-shadow:0 32px 80px rgba(0,0,0,0.6);">
    <!-- Browser chrome bar -->
    <div style="background:#13131A;padding:12px 16px;display:flex;align-items:center;gap:12px;border-bottom:1px solid #2A2A38;flex-shrink:0;">
      <div style="display:flex;gap:7px;">
        <div onclick="closePreview()" style="width:13px;height:13px;border-radius:50%;background:#FF5F57;cursor:pointer;"></div>
        <div style="width:13px;height:13px;border-radius:50%;background:#FFBD2E;"></div>
        <div style="width:13px;height:13px;border-radius:50%;background:#28C840;"></div>
      </div>
      <div style="flex:1;background:#0A0A0F;border:1px solid #2A2A38;border-radius:8px;padding:6px 14px;font-size:0.8rem;color:#8888AA;text-align:center;" id="modalUrl">aivora.ca/preview</div>
      <button onclick="closePreview()" style="background:transparent;border:1px solid #2A2A38;color:#8888AA;border-radius:8px;padding:6px 14px;cursor:pointer;font-size:0.82rem;">✕ Close</button>
    </div>
    <!-- Preview content -->
    <div id="previewContent" style="flex:1;overflow-y:auto;"></div>
  </div>
</div>
 
<!-- SERVICES -->
<section id="services">
  <div class="section-header fade-in">
    <div class="section-label">What I offer</div>
    <h2>Simple, transparent pricing</h2>
    <p class="section-sub">No hidden fees. No overcharging. Just a great website at a price that makes sense for your business.</p>
  </div>
  <div class="services-grid">
    <div class="service-card fade-in">
      <div class="service-icon">🚀</div>
      <div class="service-title">Starter Website</div>
      <div class="service-desc">Perfect for businesses that just need to get online. Includes Home, About, Services, and Contact pages.</div>
      <div class="service-price">$400 <span>one-time</span></div>
    </div>
    <div class="service-card fade-in">
      <div class="service-icon">⭐</div>
      <div class="service-title">Professional Website</div>
      <div class="service-desc">Full site with photo gallery, booking form, Google Maps embed, and basic SEO setup.</div>
      <div class="service-price">$700 <span>one-time</span></div>
    </div>
    <div class="service-card fade-in">
      <div class="service-icon">🔧</div>
      <div class="service-title">Monthly Maintenance</div>
      <div class="service-desc">I keep your site updated, secure, and running smoothly. Updates, edits, and hosting included.</div>
      <div class="service-price">$99 <span>/ month</span></div>
    </div>
    <div class="service-card fade-in">
      <div class="service-icon">📍</div>
      <div class="service-title">Google Business Setup</div>
      <div class="service-desc">Get your business on Google Maps so customers can find you when they search locally.</div>
      <div class="service-price">$149 <span>one-time</span></div>
    </div>
  </div>
</section>
 
<!-- ABOUT -->
<section id="about">
  <div class="about-grid">
    <div class="about-visual fade-in">
      <div class="section-label" style="margin-bottom:8px;">Skills</div>
      <div class="skill-row">
        <div class="skill-label"><span>Web Design</span><span>90%</span></div>
        <div class="skill-bar"><div class="skill-fill" data-width="90"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-label"><span>AI Tools</span><span>95%</span></div>
        <div class="skill-bar"><div class="skill-fill" data-width="95"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-label"><span>Local SEO</span><span>75%</span></div>
        <div class="skill-bar"><div class="skill-fill" data-width="75"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-label"><span>Mobile Optimization</span><span>85%</span></div>
        <div class="skill-bar"><div class="skill-fill" data-width="85"></div></div>
      </div>
      <div class="tools-list">
        <span class="tool-chip">Framer</span>
        <span class="tool-chip">Durable</span>
        <span class="tool-chip">HTML/CSS</span>
        <span class="tool-chip">Canva</span>
        <span class="tool-chip">ChatGPT</span>
        <span class="tool-chip">Claude AI</span>
      </div>
    </div>
    <div class="about-text fade-in">
      <div class="section-label">About me</div>
      <h2>I build websites that work for <span style="color:var(--accent2)">real businesses</span></h2>
      <p>I'm a Toronto-based web designer who helps local businesses get online fast and affordably. I use the latest AI tools to design and build websites in days — not weeks.</p>
      <p>Most web agencies charge <strong>$3,000 to $10,000</strong> for a basic website. That's not realistic for a small business. My goal is to deliver the same professional result at a price that actually makes sense.</p>
      <p>When you work with me, you get a <strong>real person</strong> who's invested in your success — not a faceless agency. I'm available, responsive, and I genuinely want your business to grow.</p>
      <a href="#contact" class="btn-primary" style="display:inline-block;margin-top:24px;">Work with me</a>
    </div>
  </div>
</section>
 
<!-- CONTACT -->
<section id="contact">
  <div class="contact-wrapper">
    <div class="fade-in">
      <div class="section-label" style="text-align:center">Contact</div>
      <h2>Let's build your website</h2>
      <p class="section-sub" style="margin:0 auto">Tell me about your business and I'll get back to you within 24 hours with a free quote.</p>
    </div>
    <form class="contact-form fade-in" id="contactForm">
      <div class="form-row">
        <div class="form-group">
          <label for="name">Your Name</label>
          <input type="text" id="name" name="name" placeholder="John Smith" required />
        </div>
        <div class="form-group">
          <label for="email">Email Address</label>
          <input type="email" id="email" name="email" placeholder="john@business.com" required />
        </div>
      </div>
      <div class="form-group">
        <label for="business">Business Name</label>
        <input type="text" id="business" name="business" placeholder="Mike's Barbershop" />
      </div>
      <div class="form-group">
        <label for="service">Service Interested In</label>
        <select id="service" name="service">
          <option value="">Select a service...</option>
          <option>Starter Website — $400</option>
          <option>Professional Website — $700</option>
          <option>Monthly Maintenance — $100/mo</option>
          <option>Google Business Setup — $150</option>
          <option>Not sure yet</option>
        </select>
      </div>
      <div class="form-group">
        <label for="message">Tell me about your business</label>
        <textarea id="message" name="message" placeholder="What does your business do? What would you like on your website?"></textarea>
      </div>
      <button type="submit" class="submit-btn" id="submitBtn">Send Message →</button>
    </form>
    <!-- SUCCESS SCREEN -->
    <div class="form-success" id="formSuccess" style="display:none;">
      <div style="font-size:3rem;margin-bottom:16px;">🎉</div>
      <h3 style="font-size:1.4rem;font-weight:800;margin-bottom:10px;color:var(--text);">Message sent successfully!</h3>
      <p style="color:var(--muted);margin-bottom:8px;">Thank you for reaching out. I've received your message and will get back to you within <strong style="color:var(--green);">24 hours</strong>.</p>
      <p style="color:var(--muted);font-size:0.9rem;">Keep an eye on your inbox at <strong id="confirmedEmail" style="color:var(--accent2);"></strong></p>
      <div style="margin-top:24px;padding:16px;background:rgba(108,99,255,0.08);border:1px solid rgba(108,99,255,0.2);border-radius:10px;">
        <p style="font-size:0.85rem;color:var(--muted);">📋 <strong style="color:var(--text);">What happens next?</strong></p>
        <p style="font-size:0.85rem;color:var(--muted);margin-top:6px;">I'll review your request, put together a free custom quote, and send it straight to your email — no pressure, no obligation.</p>
      </div>
    </div>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <span>© 2026 Aivora Web Design · Toronto, ON</span>
  <span>Aivroa.web@gmail.com</span>
</footer>
 
<script>
  // Fade in on scroll
  const fadeEls = document.querySelectorAll('.fade-in');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  fadeEls.forEach(el => observer.observe(el));
 
  // Skill bars animate when visible
  const skillObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.querySelectorAll('.skill-fill').forEach(bar => {
          bar.style.width = bar.dataset.width + '%';
        });
        skillObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.3 });
  document.querySelectorAll('.about-visual').forEach(el => skillObserver.observe(el));
 
  // Contact form — powered by Formspree
  // IMPORTANT: Replace YOUR_FORM_ID below with your actual Formspree form ID
  const FORMSPREE_ID = 'YOUR_FORM_ID';
 
  document.getElementById('contactForm').addEventListener('submit', async function(e) {
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const email = document.getElementById('email').value.trim();
    if (!name || !email) return;
 
    const btn = document.getElementById('submitBtn');
    btn.textContent = 'Sending...';
    btn.style.opacity = '0.7';
    btn.disabled = true;
 
    try {
      const formData = new FormData(this);
      const response = await fetch(`https://formspree.io/f/${FORMSPREE_ID}`, {
        method: 'POST',
        body: formData,
        headers: { 'Accept': 'application/json' }
      });
 
      if (response.ok) {
        // Show success screen
        this.style.display = 'none';
        const successEl = document.getElementById('formSuccess');
        document.getElementById('confirmedEmail').textContent = email;
        successEl.style.display = 'block';
        successEl.style.background = 'var(--surface)';
        successEl.style.border = '1px solid var(--border)';
        successEl.style.borderRadius = '14px';
        successEl.style.padding = '40px';
        successEl.style.textAlign = 'center';
      } else {
        throw new Error('Form submission failed');
      }
    } catch (err) {
      // If Formspree ID not set yet, show success anyway (for demo/testing)
      if (FORMSPREE_ID === 'YOUR_FORM_ID') {
        this.style.display = 'none';
        const successEl = document.getElementById('formSuccess');
        document.getElementById('confirmedEmail').textContent = email;
        successEl.style.display = 'block';
        successEl.style.background = 'var(--surface)';
        successEl.style.border = '1px solid var(--border)';
        successEl.style.borderRadius = '14px';
        successEl.style.padding = '40px';
        successEl.style.textAlign = 'center';
      } else {
        btn.textContent = '❌ Something went wrong — try again';
        btn.style.background = '#ef4444';
        btn.style.opacity = '1';
        btn.disabled = false;
      }
    }
  });
 
  // Demo site previews
  const demos = {
    mikes: {
      url: 'mikesbarber.ca',
      html: `<div style="font-family:'Inter',sans-serif;background:#0d0d0d;color:#f0f0f0;min-height:100%;">
        <!-- NAV -->
        <nav style="background:#111;padding:16px 5%;display:flex;justify-content:space-between;align-items:center;border-bottom:2px solid #C9A84C;position:sticky;top:0;z-index:10;">
          <span style="font-size:1.3rem;font-weight:900;letter-spacing:1px;color:#C9A84C;">✂ MIKE'S BARBERSHOP</span>
          <div style="display:flex;gap:28px;font-size:0.88rem;font-weight:600;letter-spacing:0.5px;">
            <span style="cursor:pointer;color:#C9A84C;">Home</span>
            <span style="cursor:pointer;color:#ccc;">About Us</span>
            <span style="cursor:pointer;color:#ccc;">Services</span>
            <span style="cursor:pointer;color:#ccc;">Gallery</span>
            <span style="cursor:pointer;color:#ccc;">Contact</span>
          </div>
          <button style="background:#C9A84C;color:#0d0d0d;border:none;border-radius:8px;padding:10px 22px;font-weight:800;cursor:pointer;font-size:0.88rem;letter-spacing:0.5px;">BOOK NOW</button>
        </nav>
        <!-- HERO with real photo -->
        <div style="position:relative;height:520px;overflow:hidden;">
          <img src="https://images.unsplash.com/photo-1599351431202-1e0f0137899a?w=1200&q=80" alt="Barbershop" style="width:100%;height:100%;object-fit:cover;filter:brightness(0.45);"/>
          <div style="position:absolute;inset:0;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 5%;">
            <p style="color:#C9A84C;font-size:0.82rem;letter-spacing:3px;text-transform:uppercase;margin-bottom:14px;font-weight:700;">Toronto's Premier Barbershop · Est. 2018</p>
            <h1 style="font-size:3.2rem;font-weight:900;line-height:1.05;margin-bottom:18px;text-shadow:0 2px 12px rgba(0,0,0,0.5);">Fresh Cuts.<br><span style="color:#C9A84C;">Real Style.</span></h1>
            <p style="color:#ddd;font-size:1.05rem;max-width:480px;margin-bottom:32px;line-height:1.6;">Walk-ins welcome every day. Premium haircuts, fades, and grooming services in Scarborough, ON.</p>
            <div style="display:flex;gap:16px;">
              <button style="background:#C9A84C;color:#0d0d0d;border:none;border-radius:8px;padding:14px 30px;font-size:1rem;font-weight:800;cursor:pointer;">Book Appointment</button>
              <button style="background:transparent;color:#fff;border:2px solid #C9A84C;border-radius:8px;padding:14px 30px;font-size:1rem;font-weight:600;cursor:pointer;">View Services</button>
            </div>
          </div>
        </div>
        <!-- STATS BAR -->
        <div style="background:#C9A84C;padding:20px 5%;display:grid;grid-template-columns:repeat(4,1fr);text-align:center;">
          ${[['500+','Happy Clients'],['6+','Years Experience'],['5★','Google Rating'],['Walk-ins','Always Welcome']].map(([n,l])=>`
          <div><div style="font-size:1.5rem;font-weight:900;color:#0d0d0d;">${n}</div><div style="font-size:0.78rem;color:#3a2a00;font-weight:600;">${l}</div></div>`).join('')}
        </div>
        <!-- ABOUT STRIP -->
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:0;background:#161616;">
          <img src="https://images.unsplash.com/photo-1503951914875-452162b0f3f1?w=600&q=80" alt="Barber at work" style="width:100%;height:320px;object-fit:cover;"/>
          <div style="padding:48px 40px;display:flex;flex-direction:column;justify-content:center;">
            <p style="color:#C9A84C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;margin-bottom:10px;">About Mike</p>
            <h2 style="font-size:1.8rem;font-weight:800;margin-bottom:16px;line-height:1.2;">More Than Just a Haircut</h2>
            <p style="color:#aaa;line-height:1.8;font-size:0.95rem;">Mike has been cutting hair in Scarborough for over 6 years. Known for his precision fades and attention to detail, he built this shop on one simple promise — every client leaves looking and feeling their best.</p>
            <p style="color:#aaa;line-height:1.8;font-size:0.95rem;margin-top:12px;">Whether it's your first visit or your fiftieth, you'll always get a fresh cut, great conversation, and a hot towel finish.</p>
          </div>
        </div>
        <!-- SERVICES -->
        <div style="padding:60px 5%;background:#0d0d0d;">
          <p style="color:#C9A84C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;text-align:center;margin-bottom:8px;">What We Offer</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:40px;">Our Services</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:20px;max-width:860px;margin:0 auto;">
            ${[['Classic Haircut','$30','Clean fade or scissor cut tailored to your style'],['Beard Trim','$20','Shape, line-up and condition your beard'],['Hot Towel Shave','$35','Full straight razor shave with hot towel treatment'],['Kids Cut','$20','Ages 12 and under — quick and easy'],['Hair Design','$40','Custom designs and patterns cut into your fade'],['Full Service','$55','Haircut + beard trim + hot towel combo']].map(([t,p,d])=>`
            <div style="background:#1a1a1a;border:1px solid #2a2a2a;border-top:3px solid #C9A84C;border-radius:10px;padding:24px;">
              <div style="font-size:1rem;font-weight:700;margin-bottom:6px;">${t}</div>
              <div style="color:#C9A84C;font-size:1.4rem;font-weight:800;margin-bottom:8px;">${p}</div>
              <div style="color:#888;font-size:0.85rem;line-height:1.5;">${d}</div>
            </div>`).join('')}
          </div>
        </div>
        <!-- GALLERY -->
        <div style="padding:60px 5%;background:#111;">
          <p style="color:#C9A84C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;text-align:center;margin-bottom:8px;">Our Work</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:32px;">Fresh Cuts Gallery</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;max-width:860px;margin:0 auto;">
            ${['photo-1621605815971-fbc98d665033','photo-1622286342621-4bd786c2447c','photo-1605497788044-5a32c7078486','photo-1560472355-536de3962603','photo-1634804984158-c3caa4b5e9e3','photo-1593702288056-7cc9c95e8c8a'].map(id=>`
            <img src="https://images.unsplash.com/${id}?w=300&q=75" alt="Haircut" style="width:100%;height:160px;object-fit:cover;border-radius:8px;"/>`).join('')}
          </div>
        </div>
        <!-- CONTACT -->
        <div style="padding:48px 5%;background:#C9A84C;text-align:center;">
          <h2 style="color:#0d0d0d;font-size:1.6rem;font-weight:900;margin-bottom:20px;">Come See Us</h2>
          <div style="display:flex;justify-content:center;gap:48px;flex-wrap:wrap;">
            <div><div style="font-size:1.4rem;">📍</div><div style="color:#3a2a00;font-weight:700;margin-top:6px;">123 Main St, Scarborough ON</div></div>
            <div><div style="font-size:1.4rem;">📞</div><div style="color:#3a2a00;font-weight:700;margin-top:6px;">(416) 555-0123</div></div>
            <div><div style="font-size:1.4rem;">🕐</div><div style="color:#3a2a00;font-weight:700;margin-top:6px;">Mon–Sat 9am–7pm · Sun 10am–5pm</div></div>
          </div>
        </div>
      </div>`
    },
    sunrise: {
      url: 'sunrisecleaning.ca',
      html: `<div style="font-family:'Inter',sans-serif;background:#f8fafc;color:#1e293b;min-height:100%;">
        <!-- NAV -->
        <nav style="background:#fff;padding:16px 5%;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #e2e8f0;position:sticky;top:0;z-index:10;box-shadow:0 2px 8px rgba(0,0,0,0.06);">
          <span style="font-size:1.2rem;font-weight:800;color:#0284c7;">🌅 Sunrise Cleaning Co.</span>
          <div style="display:flex;gap:24px;font-size:0.88rem;font-weight:600;color:#475569;">
            <span style="cursor:pointer;color:#0284c7;">Home</span>
            <span style="cursor:pointer;">About Us</span>
            <span style="cursor:pointer;">Services</span>
            <span style="cursor:pointer;">Gallery</span>
            <span style="cursor:pointer;">Contact</span>
          </div>
          <button style="background:#0284c7;color:#fff;border:none;border-radius:8px;padding:10px 22px;font-weight:700;cursor:pointer;">Free Quote</button>
        </nav>
        <!-- HERO -->
        <div style="position:relative;height:500px;overflow:hidden;">
          <img src="https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=1200&q=80" alt="Cleaning" style="width:100%;height:100%;object-fit:cover;filter:brightness(0.4);"/>
          <div style="position:absolute;inset:0;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 5%;">
            <p style="color:#7dd3fc;font-size:0.82rem;letter-spacing:3px;text-transform:uppercase;font-weight:700;margin-bottom:14px;">Trusted by 200+ GTA Families</p>
            <h1 style="font-size:3rem;font-weight:900;line-height:1.1;color:#fff;margin-bottom:18px;">A Cleaner Home.<br><span style="color:#38bdf8;">A Happier Life.</span></h1>
            <p style="color:#e0f2fe;font-size:1rem;max-width:500px;margin-bottom:32px;line-height:1.7;">Professional residential and commercial cleaning across the GTA. Reliable, thorough, and always on time.</p>
            <div style="display:flex;gap:14px;">
              <button style="background:#0284c7;color:#fff;border:none;border-radius:8px;padding:14px 28px;font-size:1rem;font-weight:700;cursor:pointer;">Book a Clean</button>
              <button style="background:transparent;color:#fff;border:2px solid #fff;border-radius:8px;padding:14px 28px;font-size:1rem;font-weight:600;cursor:pointer;">Our Services</button>
            </div>
          </div>
        </div>
        <!-- TRUST BAR -->
        <div style="background:#0284c7;padding:20px 5%;display:grid;grid-template-columns:repeat(4,1fr);text-align:center;color:#fff;">
          ${[['200+','Happy Clients'],['5★','Rated on Google'],['Insured','& Bonded'],['Same-Week','Availability']].map(([n,l])=>`
          <div><div style="font-size:1.4rem;font-weight:900;">${n}</div><div style="font-size:0.78rem;opacity:0.85;margin-top:2px;">${l}</div></div>`).join('')}
        </div>
        <!-- ABOUT -->
        <div style="display:grid;grid-template-columns:1fr 1fr;background:#fff;">
          <div style="padding:52px 40px;display:flex;flex-direction:column;justify-content:center;">
            <p style="color:#0284c7;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;margin-bottom:10px;">About Us</p>
            <h2 style="font-size:1.8rem;font-weight:800;margin-bottom:16px;color:#1e293b;">GTA's Most Trusted Cleaning Team</h2>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;">Founded in 2019, Sunrise Cleaning Co. was built on a simple belief — a clean home is a happy home. Our fully trained, background-checked team uses eco-friendly products that are safe for kids and pets.</p>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;margin-top:12px;">We show up on time, every time — and we don't leave until the job is done right.</p>
            <div style="display:flex;gap:16px;margin-top:24px;flex-wrap:wrap;">
              ${['✅ Eco-friendly products','✅ Background checked','✅ Fully insured','✅ Satisfaction guaranteed'].map(t=>`<span style="background:#e0f2fe;color:#0284c7;font-size:0.82rem;font-weight:600;padding:6px 12px;border-radius:20px;">${t}</span>`).join('')}
            </div>
          </div>
          <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=80" alt="Cleaning team" style="width:100%;height:360px;object-fit:cover;"/>
        </div>
        <!-- SERVICES -->
        <div style="padding:60px 5%;background:#f8fafc;">
          <p style="color:#0284c7;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;text-align:center;margin-bottom:8px;">Pricing</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:40px;color:#1e293b;">Our Cleaning Packages</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:20px;max-width:860px;margin:0 auto;">
            ${[['🧹','Basic Clean','$120','Bathrooms, kitchen surfaces, vacuum all floors, mop hard floors, empty trash'],['✨','Deep Clean','$220','Everything in Basic + inside oven, fridge, baseboards, window sills, inside cabinets'],['📦','Move In / Out','$320','Full top-to-bottom clean — perfect for tenants, landlords, and new homeowners']].map(([icon,t,p,d])=>`
            <div style="background:#fff;border:1px solid #e0f2fe;border-top:4px solid #0284c7;border-radius:12px;padding:28px;text-align:center;box-shadow:0 2px 12px rgba(0,0,0,0.04);">
              <div style="font-size:2rem;margin-bottom:12px;">${icon}</div>
              <div style="font-size:1rem;font-weight:700;color:#0284c7;margin-bottom:8px;">${t}</div>
              <div style="font-size:1.8rem;font-weight:900;margin-bottom:12px;color:#1e293b;">${p}</div>
              <div style="color:#64748b;font-size:0.85rem;line-height:1.6;">${d}</div>
            </div>`).join('')}
          </div>
        </div>
        <!-- GALLERY -->
        <div style="padding:60px 5%;background:#fff;">
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:32px;color:#1e293b;">Before & After</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;max-width:860px;margin:0 auto;">
            ${['photo-1584820927498-cfe5211fd8bf','photo-1556909114-f6e7ad7d3136','photo-1527515637462-cff94aca7b82','photo-1556909172-54557c7e4fb7','photo-1585771724684-38269d6639fd','photo-1563453392212-326f5e854473'].map(id=>`
            <img src="https://images.unsplash.com/${id}?w=300&q=75" alt="Clean home" style="width:100%;height:160px;object-fit:cover;border-radius:8px;"/>`).join('')}
          </div>
        </div>
        <!-- CONTACT -->
        <div style="padding:48px 5%;background:#0284c7;text-align:center;color:#fff;">
          <h2 style="font-size:1.6rem;font-weight:900;margin-bottom:20px;">Ready for a Cleaner Home?</h2>
          <div style="display:flex;justify-content:center;gap:48px;flex-wrap:wrap;">
            <div><div style="font-size:1.3rem;">📞</div><div style="font-weight:700;margin-top:6px;">(416) 555-0199</div></div>
            <div><div style="font-size:1.3rem;">✉️</div><div style="font-weight:700;margin-top:6px;">hello@sunrisecleaning.ca</div></div>
            <div><div style="font-size:1.3rem;">📍</div><div style="font-weight:700;margin-top:6px;">Serving all of the GTA</div></div>
          </div>
        </div>
      </div>`
    },
    bella: {
      url: 'bellanailsspa.ca',
      html: `<div style="font-family:'Inter',sans-serif;background:#fdf2f8;color:#1e293b;min-height:100%;">
        <!-- NAV -->
        <nav style="background:#fff;padding:16px 5%;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #fce7f3;position:sticky;top:0;z-index:10;box-shadow:0 2px 8px rgba(219,39,119,0.06);">
          <span style="font-size:1.2rem;font-weight:800;color:#db2777;">💅 Bella Nails & Spa</span>
          <div style="display:flex;gap:24px;font-size:0.88rem;font-weight:600;color:#9d174d;">
            <span style="cursor:pointer;color:#db2777;">Home</span>
            <span style="cursor:pointer;color:#64748b;">About Us</span>
            <span style="cursor:pointer;color:#64748b;">Services</span>
            <span style="cursor:pointer;color:#64748b;">Gallery</span>
            <span style="cursor:pointer;color:#64748b;">Contact</span>
          </div>
          <button style="background:#db2777;color:#fff;border:none;border-radius:8px;padding:10px 22px;font-weight:700;cursor:pointer;">Book Now</button>
        </nav>
        <!-- HERO -->
        <div style="position:relative;height:480px;overflow:hidden;">
          <img src="https://images.unsplash.com/photo-1604654894610-df63bc536371?w=1200&q=80" alt="Nail salon" style="width:100%;height:100%;object-fit:cover;filter:brightness(0.45);"/>
          <div style="position:absolute;inset:0;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 5%;">
            <p style="color:#fbcfe8;font-size:0.82rem;letter-spacing:3px;text-transform:uppercase;font-weight:700;margin-bottom:14px;">Premium Nail Studio · Toronto, ON</p>
            <h1 style="font-size:3rem;font-weight:900;line-height:1.1;color:#fff;margin-bottom:18px;">Beautiful Nails.<br><span style="color:#f9a8d4;">Every Time.</span></h1>
            <p style="color:#fce7f3;font-size:1rem;max-width:460px;margin-bottom:32px;line-height:1.7;">Luxury nail care in a clean, relaxing environment. Walk-ins welcome — appointments preferred.</p>
            <button style="background:#db2777;color:#fff;border:none;border-radius:8px;padding:14px 32px;font-size:1rem;font-weight:700;cursor:pointer;">Book an Appointment</button>
          </div>
        </div>
        <!-- ABOUT -->
        <div style="display:grid;grid-template-columns:1fr 1fr;background:#fff;">
          <img src="https://images.unsplash.com/photo-1519014816548-bf5fe059798b?w=600&q=80" alt="Nail art" style="width:100%;height:340px;object-fit:cover;"/>
          <div style="padding:48px 40px;display:flex;flex-direction:column;justify-content:center;">
            <p style="color:#db2777;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;margin-bottom:10px;">About Bella</p>
            <h2 style="font-size:1.7rem;font-weight:800;margin-bottom:16px;color:#831843;line-height:1.2;">Where Self-Care Meets Art</h2>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;">Bella Nails & Spa was founded by nail artist Bella Chen in 2020 with one vision — to create a space where every client feels pampered, valued, and leaves absolutely glowing.</p>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;margin-top:12px;">From classic manicures to intricate nail art, our certified technicians use only premium, non-toxic products. Your safety and satisfaction come first.</p>
          </div>
        </div>
        <!-- SERVICES -->
        <div style="padding:60px 5%;background:#fdf2f8;">
          <p style="color:#db2777;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;text-align:center;margin-bottom:8px;">Menu</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:40px;color:#831843;">Services & Pricing</h2>
          <div style="display:grid;grid-template-columns:repeat(2,1fr);gap:14px;max-width:760px;margin:0 auto;">
            ${[['Classic Manicure','$35','Shape, buff, cuticle care + polish'],['Gel Manicure','$50','Long-lasting gel colour — chip free for 3+ weeks'],['Classic Pedicure','$45','Soak, scrub, massage + polish'],['Gel Pedicure','$60','Premium pedicure with long-wear gel'],['Acrylic Full Set','$75','Full set of natural-looking acrylic extensions'],['Nail Art','$5+ / nail','Custom designs, gems, patterns & more']].map(([s,p,d])=>`
            <div style="background:#fff;border:1px solid #fce7f3;border-radius:10px;padding:18px 20px;display:flex;justify-content:space-between;align-items:flex-start;">
              <div><div style="font-weight:700;margin-bottom:4px;">${s}</div><div style="color:#9d174d;font-size:0.82rem;">${d}</div></div>
              <div style="color:#db2777;font-weight:800;font-size:1.1rem;white-space:nowrap;margin-left:12px;">${p}</div>
            </div>`).join('')}
          </div>
        </div>
        <!-- GALLERY -->
        <div style="padding:60px 5%;background:#fff;">
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:32px;color:#831843;">Nail Gallery</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;max-width:860px;margin:0 auto;">
            ${['photo-1604654894610-df63bc536371','photo-1604654894610-df63bc536371','photo-1519014816548-bf5fe059798b','photo-1604654894610-df63bc536371','photo-1519014816548-bf5fe059798b','photo-1604654894610-df63bc536371'].map((id,i)=>`
            <img src="https://images.unsplash.com/${i%2===0?'photo-1604654894610-df63bc536371':'photo-1519014816548-bf5fe059798b'}?w=300&q=75&sig=${i}" alt="Nail art" style="width:100%;height:160px;object-fit:cover;border-radius:8px;"/>`).join('')}
          </div>
        </div>
        <!-- FOOTER -->
        <div style="padding:40px 5%;background:#db2777;text-align:center;color:#fff;">
          <h2 style="font-size:1.4rem;font-weight:900;margin-bottom:16px;">Visit Us Today</h2>
          <div style="display:flex;justify-content:center;gap:40px;flex-wrap:wrap;">
            <div><div style="font-size:1.2rem;">📍</div><div style="font-weight:600;margin-top:4px;">456 Queen St E, Toronto ON</div></div>
            <div><div style="font-size:1.2rem;">📞</div><div style="font-weight:600;margin-top:4px;">(416) 555-0177</div></div>
            <div><div style="font-size:1.2rem;">🕐</div><div style="font-weight:600;margin-top:4px;">Tue–Sun: 10am – 7pm</div></div>
          </div>
        </div>
      </div>`
    },
    cafe: {
      url: 'cafemaison.ca',
      html: `<div style="font-family:'Georgia',serif;background:#F5EFE6;color:#2C1A0E;min-height:100%;">
        <!-- NAV -->
        <nav style="background:#2C1A0E;padding:16px 5%;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:10;">
          <span style="font-size:1.2rem;font-weight:700;color:#D4A96A;letter-spacing:1px;">☕ Café Maison</span>
          <div style="display:flex;gap:24px;font-size:0.88rem;font-family:'Inter',sans-serif;font-weight:600;">
            <span style="cursor:pointer;color:#D4A96A;">Home</span>
            <span style="cursor:pointer;color:#C8B8A2;">Menu</span>
            <span style="cursor:pointer;color:#C8B8A2;">About Us</span>
            <span style="cursor:pointer;color:#C8B8A2;">Gallery</span>
            <span style="cursor:pointer;color:#C8B8A2;">Contact</span>
          </div>
          <button style="background:#D4A96A;color:#2C1A0E;border:none;border-radius:6px;padding:10px 20px;font-weight:700;cursor:pointer;font-family:'Inter',sans-serif;">Reserve a Table</button>
        </nav>
        <!-- HERO -->
        <div style="position:relative;height:500px;overflow:hidden;">
          <img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?w=1200&q=80" alt="Cafe interior" style="width:100%;height:100%;object-fit:cover;filter:brightness(0.5);"/>
          <div style="position:absolute;inset:0;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 5%;">
            <p style="color:#D4A96A;font-size:0.8rem;letter-spacing:3px;text-transform:uppercase;font-family:'Inter',sans-serif;font-weight:700;margin-bottom:14px;">French-Canadian Café · Toronto, ON</p>
            <h1 style="font-size:3rem;font-weight:700;line-height:1.15;color:#F5EFE6;margin-bottom:18px;text-shadow:0 2px 16px rgba(0,0,0,0.4);">Where Every Cup<br><em style="color:#D4A96A;">Tells a Story.</em></h1>
            <p style="color:#D9C9B5;font-size:1rem;max-width:460px;margin-bottom:32px;line-height:1.7;font-family:'Inter',sans-serif;">Handcrafted coffee, fresh pastries, and warm French-Canadian hospitality — made with love daily.</p>
            <div style="display:flex;gap:14px;">
              <button style="background:#D4A96A;color:#2C1A0E;border:none;border-radius:6px;padding:14px 28px;font-size:1rem;font-weight:700;cursor:pointer;font-family:'Inter',sans-serif;">Reserve a Table</button>
              <button style="background:transparent;color:#F5EFE6;border:2px solid #D4A96A;border-radius:6px;padding:14px 28px;font-size:1rem;font-weight:600;cursor:pointer;font-family:'Inter',sans-serif;">See Our Menu</button>
            </div>
          </div>
        </div>
        <!-- ABOUT -->
        <div style="display:grid;grid-template-columns:1fr 1fr;background:#EDE0D0;">
          <div style="padding:52px 44px;display:flex;flex-direction:column;justify-content:center;">
            <p style="color:#8B5E3C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-family:'Inter',sans-serif;font-weight:700;margin-bottom:10px;">Our Story</p>
            <h2 style="font-size:1.8rem;font-weight:700;margin-bottom:16px;color:#2C1A0E;line-height:1.2;">A Little Corner of Paris in Toronto</h2>
            <p style="color:#6B4A2A;line-height:1.9;font-size:0.95rem;font-family:'Inter',sans-serif;">Café Maison was born in 2017 when founder Marie Lefebvre wanted to bring the warmth of a French neighbourhood café to Toronto's west end. Every recipe is inspired by her grandmother's kitchen in Montréal.</p>
            <p style="color:#6B4A2A;line-height:1.9;font-size:0.95rem;font-family:'Inter',sans-serif;margin-top:12px;">We bake everything fresh every morning. Our coffee beans are sourced from small ethical farms. Come for the coffee, stay for the croissants.</p>
          </div>
          <img src="https://images.unsplash.com/photo-1445116572660-236099ec97a0?w=600&q=80" alt="Coffee and pastries" style="width:100%;height:360px;object-fit:cover;"/>
        </div>
        <!-- COFFEE MENU -->
        <div style="padding:60px 5%;background:#F5EFE6;">
          <p style="color:#8B5E3C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-family:'Inter',sans-serif;font-weight:700;text-align:center;margin-bottom:8px;">Drinks</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:700;margin-bottom:40px;color:#2C1A0E;">Our Coffee Menu</h2>
          <div style="display:grid;grid-template-columns:repeat(2,1fr);gap:16px;max-width:860px;margin:0 auto 48px;">
            ${[['Espresso','$3.50','Single or double shot — rich and bold'],['Americano','$4.00','Espresso + hot water — smooth and clean'],['Café Au Lait','$4.75','Espresso with steamed whole milk'],['Cappuccino','$5.00','Equal parts espresso, steamed & foamed milk'],['Flat White','$5.25','Velvety microfoam over a double ristretto'],['Café Maison Latte','$5.75','Our signature — vanilla, hazelnut & oat milk'],['Cold Brew','$5.00','12-hour steeped, served over ice'],['Matcha Latte','$5.50','Ceremonial grade matcha with oat milk'],['Chai Latte','$5.00','House-spiced chai with steamed milk'],['Hot Chocolate','$4.50','Rich Belgian chocolate — a Maison classic']].map(([n,p,d])=>`
            <div style="background:#EDE0D0;border-radius:10px;padding:16px 20px;display:flex;justify-content:space-between;align-items:flex-start;border-left:3px solid #D4A96A;">
              <div><div style="font-weight:700;font-size:0.95rem;margin-bottom:3px;">${n}</div><div style="color:#8B5E3C;font-size:0.82rem;font-family:'Inter',sans-serif;">${d}</div></div>
              <div style="color:#6B4A2A;font-weight:700;font-family:'Inter',sans-serif;white-space:nowrap;margin-left:12px;">${p}</div>
            </div>`).join('')}
          </div>
          <p style="color:#8B5E3C;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-family:'Inter',sans-serif;font-weight:700;text-align:center;margin-bottom:8px;">Food</p>
          <h2 style="text-align:center;font-size:1.6rem;font-weight:700;margin-bottom:32px;color:#2C1A0E;">Freshly Baked Daily</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:16px;max-width:860px;margin:0 auto;">
            ${[['Croissant au Beurre','$3.75','Classic buttery croissant'],['Pain au Chocolat','$4.25','Flaky pastry with dark chocolate'],['Croque Monsieur','$12','Ham & gruyère on brioche'],['Soupe du Jour','$9','Chef\'s daily French-inspired soup'],['Quiche Lorraine','$11','Bacon, gruyère, silky custard'],['Salade Niçoise','$14','Tuna, olives, egg, green beans']].map(([n,p,d])=>`
            <div style="background:#EDE0D0;border-radius:10px;padding:20px;text-align:center;">
              <div style="font-weight:700;margin-bottom:4px;">${n}</div>
              <div style="color:#D4A96A;font-weight:700;font-family:'Inter',sans-serif;margin-bottom:6px;">${p}</div>
              <div style="color:#8B5E3C;font-size:0.82rem;font-family:'Inter',sans-serif;">${d}</div>
            </div>`).join('')}
          </div>
        </div>
        <!-- GALLERY -->
        <div style="padding:60px 5%;background:#EDE0D0;">
          <h2 style="text-align:center;font-size:1.8rem;font-weight:700;margin-bottom:32px;color:#2C1A0E;">Our Space</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;max-width:860px;margin:0 auto;">
            ${['photo-1501339847302-ac426a4a7cbb','photo-1445116572660-236099ec97a0','photo-1509042239860-f550ce710b93','photo-1495474472287-4d71bcdd2085','photo-1514432324607-a09d9b4aefdd','photo-1521302200778-33500795e128'].map(id=>`
            <img src="https://images.unsplash.com/${id}?w=300&q=75" alt="Cafe" style="width:100%;height:160px;object-fit:cover;border-radius:8px;"/>`).join('')}
          </div>
        </div>
        <!-- CONTACT -->
        <div style="padding:48px 5%;background:#2C1A0E;text-align:center;">
          <h2 style="color:#D4A96A;font-size:1.5rem;font-weight:700;margin-bottom:20px;">Come Visit Us</h2>
          <div style="display:flex;justify-content:center;gap:48px;flex-wrap:wrap;font-family:'Inter',sans-serif;">
            <div><div style="font-size:1.3rem;">📍</div><div style="color:#C8B8A2;margin-top:6px;font-weight:600;">789 King St W, Toronto ON</div></div>
            <div><div style="font-size:1.3rem;">🕐</div><div style="color:#C8B8A2;margin-top:6px;font-weight:600;">Mon–Fri 7am–6pm · Sat–Sun 8am–5pm</div></div>
            <div><div style="font-size:1.3rem;">📞</div><div style="color:#C8B8A2;margin-top:6px;font-weight:600;">(416) 555-0188</div></div>
          </div>
        </div>
      </div>`
    },
    peak: {
      url: 'peakrenovations.ca',
      html: `<div style="font-family:'Inter',sans-serif;background:#f8fafc;color:#1e293b;min-height:100%;">
        <!-- NAV -->
        <nav style="background:#fff;padding:16px 5%;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #e2e8f0;position:sticky;top:0;z-index:10;box-shadow:0 2px 8px rgba(0,0,0,0.06);">
          <span style="font-size:1.2rem;font-weight:800;color:#b45309;">🔨 Peak Renovations</span>
          <div style="display:flex;gap:24px;font-size:0.88rem;font-weight:600;color:#475569;">
            <span style="cursor:pointer;color:#b45309;">Home</span>
            <span style="cursor:pointer;">About Us</span>
            <span style="cursor:pointer;">Services</span>
            <span style="cursor:pointer;">Gallery</span>
            <span style="cursor:pointer;">Contact</span>
          </div>
          <button style="background:#b45309;color:#fff;border:none;border-radius:8px;padding:10px 22px;font-weight:700;cursor:pointer;">Free Quote</button>
        </nav>
        <!-- HERO -->
        <div style="position:relative;height:500px;overflow:hidden;">
          <img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=1200&q=80" alt="Renovation" style="width:100%;height:100%;object-fit:cover;filter:brightness(0.4);"/>
          <div style="position:absolute;inset:0;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 5%;">
            <p style="color:#fcd34d;font-size:0.82rem;letter-spacing:3px;text-transform:uppercase;font-weight:700;margin-bottom:14px;">Licensed & Insured · Serving the GTA Since 2015</p>
            <h1 style="font-size:3rem;font-weight:900;line-height:1.1;color:#fff;margin-bottom:18px;">Built Right.<br><span style="color:#fbbf24;">Built to Last.</span></h1>
            <p style="color:#e2e8f0;font-size:1rem;max-width:500px;margin-bottom:32px;line-height:1.7;">Full-service home renovation contractor. Bathrooms, kitchens, basements and more — done on time and on budget.</p>
            <div style="display:flex;gap:14px;">
              <button style="background:#b45309;color:#fff;border:none;border-radius:8px;padding:14px 28px;font-size:1rem;font-weight:700;cursor:pointer;">Get a Free Estimate</button>
              <button style="background:transparent;color:#fff;border:2px solid #fff;border-radius:8px;padding:14px 28px;font-size:1rem;font-weight:600;cursor:pointer;">Our Work</button>
            </div>
          </div>
        </div>
        <!-- TRUST BAR -->
        <div style="background:#b45309;padding:20px 5%;display:grid;grid-template-columns:repeat(4,1fr);text-align:center;color:#fff;">
          ${[['150+','Projects Done'],['10yr','Warranty'],['5★','Google Rating'],['Licensed','& Insured']].map(([n,l])=>`
          <div><div style="font-size:1.4rem;font-weight:900;">${n}</div><div style="font-size:0.78rem;opacity:0.85;margin-top:2px;">${l}</div></div>`).join('')}
        </div>
        <!-- ABOUT -->
        <div style="display:grid;grid-template-columns:1fr 1fr;background:#fff;">
          <div style="padding:52px 40px;display:flex;flex-direction:column;justify-content:center;">
            <p style="color:#b45309;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;margin-bottom:10px;">About Peak</p>
            <h2 style="font-size:1.8rem;font-weight:800;margin-bottom:16px;color:#1e293b;">Toronto's Trusted Renovation Crew</h2>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;">Peak Renovations was founded in 2015 by contractor Dave Russo with one goal — to give GTA homeowners a renovation experience they could actually trust. No hidden fees, no cut corners, no excuses.</p>
            <p style="color:#64748b;line-height:1.8;font-size:0.95rem;margin-top:12px;">Our team of certified tradespeople handles everything from design to final walkthrough. We keep you informed every step of the way.</p>
            <div style="display:flex;gap:12px;margin-top:24px;flex-wrap:wrap;">
              ${['✅ Licensed & insured','✅ Free estimates','✅ On-time delivery','✅ 10-year warranty'].map(t=>`<span style="background:#fef3c7;color:#b45309;font-size:0.82rem;font-weight:600;padding:6px 12px;border-radius:20px;">${t}</span>`).join('')}
            </div>
          </div>
          <img src="https://images.unsplash.com/photo-1556909114-f6e7ad7d3136?w=600&q=80" alt="Renovation work" style="width:100%;height:360px;object-fit:cover;"/>
        </div>
        <!-- SERVICES -->
        <div style="padding:60px 5%;background:#f8fafc;">
          <p style="color:#b45309;font-size:0.78rem;letter-spacing:2px;text-transform:uppercase;font-weight:700;text-align:center;margin-bottom:8px;">What We Do</p>
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:40px;color:#1e293b;">Our Services</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:20px;max-width:860px;margin:0 auto;">
            ${[['🛁','Bathroom Remodel','From cosmetic refresh to full gut — new tile, fixtures, vanity and more'],['🍳','Kitchen Renovation','Custom cabinets, stone counters, backsplash, appliance installation'],['🏠','Basement Finishing','Transform unused space into a legal bedroom, gym, or rec room'],['🪟','Windows & Doors','Energy-efficient replacements with professional installation'],['🎨','Interior Painting','Full interior paint service — ceilings, trim, walls done right'],['🏗️','General Contracting','Design-build projects managed start to finish by our crew']].map(([icon,t,d])=>`
            <div style="background:#fff;border:1px solid #fef3c7;border-top:4px solid #b45309;border-radius:12px;padding:28px;box-shadow:0 2px 8px rgba(0,0,0,0.04);">
              <div style="font-size:2rem;margin-bottom:14px;">${icon}</div>
              <div style="font-weight:700;font-size:1rem;margin-bottom:8px;">${t}</div>
              <div style="color:#64748b;font-size:0.85rem;line-height:1.6;">${d}</div>
            </div>`).join('')}
          </div>
        </div>
        <!-- GALLERY -->
        <div style="padding:60px 5%;background:#fff;">
          <h2 style="text-align:center;font-size:1.8rem;font-weight:800;margin-bottom:32px;color:#1e293b;">Recent Projects</h2>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;max-width:860px;margin:0 auto;">
            ${['photo-1600585154340-be6161a56a0c','photo-1556909114-f6e7ad7d3136','photo-1503387762-592deb58ef4e','photo-1507089947368-19c1da9775ae','photo-1513694203232-719a280e022f','photo-1505843513577-22bb7d21e455'].map(id=>`
            <img src="https://images.unsplash.com/${id}?w=300&q=75" alt="Renovation project" style="width:100%;height:160px;object-fit:cover;border-radius:8px;"/>`).join('')}
          </div>
        </div>
        <!-- CONTACT -->
        <div style="padding:48px 5%;background:#b45309;text-align:center;color:#fff;">
          <h2 style="font-size:1.6rem;font-weight:900;margin-bottom:20px;">Ready to Start Your Project?</h2>
          <div style="display:flex;justify-content:center;gap:48px;flex-wrap:wrap;">
            <div><div style="font-size:1.3rem;">📞</div><div style="font-weight:700;margin-top:6px;">(416) 555-0145</div></div>
            <div><div style="font-size:1.3rem;">✉️</div><div style="font-weight:700;margin-top:6px;">info@peakrenovations.ca</div></div>
            <div><div style="font-size:1.3rem;">📍</div><div style="font-weight:700;margin-top:6px;">Serving All of the GTA</div></div>
          </div>
        </div>
      </div>`
    }
  };
 
  function openPreview(key) {
    const demo = demos[key];
    document.getElementById('modalUrl').textContent = demo.url;
    document.getElementById('previewContent').innerHTML = demo.html;
    const modal = document.getElementById('previewModal');
    modal.style.display = 'flex';
    document.body.style.overflow = 'hidden';
  }
 
  function closePreview() {
    document.getElementById('previewModal').style.display = 'none';
    document.body.style.overflow = '';
  }
 
  document.getElementById('previewModal').addEventListener('click', function(e) {
    if (e.target === this) closePreview();
  });
 
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') closePreview();
  });
 
  // Smooth nav highlight
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 120) current = s.getAttribute('id');
    });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? 'var(--text)' : '';
    });
  });
</script>
</body>
</html>
