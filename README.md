<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FinanceFlow Pro — Master Your Money</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ink:       #0D1117;
    --paper:     #F5F0E8;
    --cream:     #EDE8DC;
    --gold:      #C9A84C;
    --gold-light:#E8D5A3;
    --gold-pale: #FBF6EC;
    --green:     #2D6A4F;
    --green-lt:  #D8F3DC;
    --red:       #C1121F;
    --red-lt:    #FFE5E7;
    --blue:      #1B4F72;
    --blue-lt:   #D6EAF8;
    --muted:     #6B7280;
    --border:    rgba(13,17,23,0.12);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--paper);
    color: var(--ink);
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* ── NOISE TEXTURE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 9999; opacity: 0.4;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.1rem 3rem;
    background: rgba(245,240,232,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem; font-weight: 700;
    letter-spacing: -0.02em;
    color: var(--ink);
    text-decoration: none;
  }
  .nav-logo span { color: var(--gold); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    font-size: 0.875rem; font-weight: 500;
    color: var(--muted); text-decoration: none;
    transition: color .2s;
  }
  .nav-links a:hover { color: var(--ink); }
  .nav-cta {
    background: var(--ink); color: var(--paper);
    padding: 0.55rem 1.4rem; border-radius: 4px;
    font-size: 0.875rem; font-weight: 600;
    text-decoration: none;
    transition: background .2s, transform .15s;
  }
  .nav-cta:hover { background: var(--gold); color: var(--ink); transform: translateY(-1px); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: grid; place-items: center;
    padding: 8rem 3rem 5rem;
    position: relative;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 20% 50%, rgba(201,168,76,0.10) 0%, transparent 60%),
      radial-gradient(ellipse 60% 80% at 85% 30%, rgba(45,106,79,0.08) 0%, transparent 55%),
      radial-gradient(ellipse 50% 50% at 60% 80%, rgba(27,79,114,0.07) 0%, transparent 50%);
  }

  /* Decorative lines */
  .hero-bg::before {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 70% 70% at 50% 50%, black 40%, transparent 80%);
  }

  .hero-inner {
    max-width: 820px; text-align: center;
    position: relative; z-index: 1;
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: var(--gold-pale);
    border: 1px solid var(--gold-light);
    color: #7A5C1E;
    padding: 0.35rem 1rem; border-radius: 100px;
    font-size: 0.8rem; font-weight: 600;
    letter-spacing: 0.06em; text-transform: uppercase;
    margin-bottom: 2rem;
    animation: fadeUp 0.6s ease both;
  }
  .hero-badge::before { content: '✦'; color: var(--gold); }

  .hero-h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 7vw, 5.5rem);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -0.03em;
    color: var(--ink);
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s 0.1s ease both;
  }
  .hero-h1 em {
    font-style: italic;
    color: var(--gold);
    position: relative;
  }
  .hero-h1 em::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0; height: 3px;
    background: var(--gold);
    border-radius: 2px;
    transform: scaleX(0);
    transform-origin: left;
    animation: underlineGrow 0.8s 0.8s ease forwards;
  }

  .hero-sub {
    font-size: 1.15rem; color: var(--muted); font-weight: 400;
    max-width: 560px; margin: 0 auto 2.5rem;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-actions {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }
  .btn-primary {
    background: var(--ink); color: var(--paper);
    padding: 0.9rem 2.2rem; border-radius: 6px;
    font-size: 1rem; font-weight: 600;
    text-decoration: none; display: inline-flex; align-items: center; gap: 0.5rem;
    transition: all .2s; box-shadow: 0 4px 20px rgba(13,17,23,0.2);
  }
  .btn-primary:hover { background: var(--gold); color: var(--ink); transform: translateY(-2px); box-shadow: 0 8px 30px rgba(201,168,76,0.3); }
  .btn-secondary {
    background: transparent; color: var(--ink);
    padding: 0.9rem 2rem; border-radius: 6px;
    border: 1.5px solid var(--border);
    font-size: 1rem; font-weight: 500;
    text-decoration: none; display: inline-flex; align-items: center; gap: 0.5rem;
    transition: all .2s;
  }
  .btn-secondary:hover { border-color: var(--ink); background: var(--cream); }

  .hero-proof {
    margin-top: 3rem;
    display: flex; align-items: center; justify-content: center; gap: 2rem;
    flex-wrap: wrap;
    animation: fadeUp 0.6s 0.4s ease both;
  }
  .proof-item {
    display: flex; align-items: center; gap: 0.5rem;
    font-size: 0.85rem; color: var(--muted);
  }
  .proof-item .icon { font-size: 1rem; }

  /* ── SPREADSHEET PREVIEW ── */
  .preview-section {
    padding: 2rem 3rem 6rem;
    display: flex; justify-content: center;
  }
  .preview-wrapper {
    max-width: 900px; width: 100%;
    background: var(--ink);
    border-radius: 12px;
    padding: 1.5rem;
    box-shadow: 0 40px 80px rgba(13,17,23,0.25), 0 0 0 1px rgba(255,255,255,0.05);
    position: relative;
    animation: fadeUp 0.8s 0.5s ease both;
  }
  .preview-topbar {
    display: flex; align-items: center; gap: 0.5rem;
    margin-bottom: 1rem;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #FF5F57; }
  .dot-y { background: #FFBD2E; }
  .dot-g { background: #28CA41; }
  .preview-filename {
    margin-left: 0.5rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem; color: rgba(255,255,255,0.4);
  }
  .preview-tabs {
    display: flex; gap: 2px; margin-bottom: 0.75rem; flex-wrap: wrap;
  }
  .tab {
    padding: 0.3rem 0.9rem; border-radius: 4px 4px 0 0;
    font-size: 0.72rem; font-weight: 500; cursor: pointer;
    transition: all .2s;
  }
  .tab.active { background: #1E2A38; color: #F5F0E8; }
  .tab:not(.active) { background: rgba(255,255,255,0.06); color: rgba(255,255,255,0.4); }
  .tab:not(.active):hover { background: rgba(255,255,255,0.1); color: rgba(255,255,255,0.7); }

  .spreadsheet-grid {
    background: #1E2A38; border-radius: 0 6px 6px 6px;
    overflow: hidden; font-family: 'DM Mono', monospace; font-size: 0.72rem;
  }
  .sheet-header-row {
    display: grid; grid-template-columns: 80px repeat(5, 1fr);
    background: #162030;
  }
  .sh-cell {
    padding: 0.4rem 0.6rem; color: rgba(255,255,255,0.35);
    border-right: 1px solid rgba(255,255,255,0.05);
    border-bottom: 1px solid rgba(255,255,255,0.05);
    font-size: 0.65rem; text-align: center;
  }
  .s-row {
    display: grid; grid-template-columns: 80px repeat(5, 1fr);
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }
  .s-row:hover { background: rgba(255,255,255,0.02); }
  .s-cell {
    padding: 0.45rem 0.6rem;
    border-right: 1px solid rgba(255,255,255,0.04);
    color: rgba(255,255,255,0.75);
    white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .s-cell.row-num { color: rgba(255,255,255,0.25); font-size: 0.65rem; text-align: center; }
  .s-cell.label { color: rgba(255,255,255,0.55); font-size: 0.68rem; }
  .s-cell.income { color: #52D68A; font-weight: 500; }
  .s-cell.expense { color: #FF7070; font-weight: 500; }
  .s-cell.profit { color: #FFD166; font-weight: 700; }
  .s-cell.header-cell {
    background: #2E86AB; color: white; font-weight: 500; font-size: 0.68rem;
  }
  .s-cell.kpi-label {
    background: #243447; color: rgba(255,255,255,0.6); font-size: 0.68rem;
  }
  .s-cell.kpi-value {
    background: #243447; font-weight: 700; font-size: 0.8rem;
  }

  /* ── FEATURES ── */
  .section { padding: 6rem 3rem; }
  .section-inner { max-width: 1100px; margin: 0 auto; }

  .section-label {
    font-size: 0.75rem; font-weight: 600; letter-spacing: 0.1em;
    text-transform: uppercase; color: var(--gold);
    margin-bottom: 0.75rem;
  }
  .section-h2 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700; line-height: 1.15;
    letter-spacing: -0.02em; color: var(--ink);
    margin-bottom: 1rem;
  }
  .section-sub { font-size: 1.05rem; color: var(--muted); max-width: 520px; }

  .features-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5px;
    margin-top: 4rem;
    border: 1.5px solid var(--border);
    border-radius: 10px; overflow: hidden;
  }
  .feature-card {
    background: var(--paper);
    padding: 2.2rem;
    transition: background .2s;
    position: relative;
  }
  .feature-card:hover { background: var(--gold-pale); }
  .feature-card::after {
    content: '';
    position: absolute; inset: 0;
    border: 1.5px solid var(--border);
    pointer-events: none;
  }
  .feature-icon {
    font-size: 2rem; margin-bottom: 1rem;
    display: block;
  }
  .feature-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem; font-weight: 700;
    color: var(--ink); margin-bottom: 0.5rem;
  }
  .feature-desc { font-size: 0.9rem; color: var(--muted); line-height: 1.65; }

  /* ── WHAT'S INSIDE ── */
  .inside-section {
    background: var(--ink);
    padding: 6rem 3rem;
    color: var(--paper);
  }
  .inside-inner { max-width: 1100px; margin: 0 auto; }
  .inside-section .section-h2 { color: var(--paper); }
  .inside-section .section-sub { color: rgba(245,240,232,0.55); }

  .sheets-list {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1rem; margin-top: 3rem;
  }
  .sheet-card {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 8px; padding: 1.8rem;
    position: relative; overflow: hidden;
    transition: all .2s;
  }
  .sheet-card:hover {
    background: rgba(255,255,255,0.08);
    border-color: rgba(201,168,76,0.4);
    transform: translateY(-2px);
  }
  .sheet-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
  }
  .sheet-card.c1::before { background: linear-gradient(90deg, #2E86AB, #52D68A); }
  .sheet-card.c2::before { background: linear-gradient(90deg, #FF7070, #FFB347); }
  .sheet-card.c3::before { background: linear-gradient(90deg, #52D68A, #2E86AB); }
  .sheet-card.c4::before { background: linear-gradient(90deg, #FFD166, #C9A84C); }
  .sheet-card.c5::before { background: linear-gradient(90deg, #A78BFA, #818CF8); }

  .sheet-emoji { font-size: 1.8rem; margin-bottom: 0.8rem; display: block; }
  .sheet-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem; font-weight: 700;
    color: var(--paper); margin-bottom: 0.4rem;
  }
  .sheet-desc { font-size: 0.85rem; color: rgba(245,240,232,0.5); line-height: 1.6; }
  .sheet-bullets { list-style: none; margin-top: 0.8rem; }
  .sheet-bullets li {
    font-size: 0.8rem; color: rgba(245,240,232,0.5);
    padding: 0.2rem 0; display: flex; align-items: flex-start; gap: 0.4rem;
  }
  .sheet-bullets li::before { content: '–'; color: var(--gold); flex-shrink: 0; }

  /* ── PRICING ── */
  .pricing-section { padding: 6rem 3rem; background: var(--cream); }
  .pricing-inner { max-width: 800px; margin: 0 auto; text-align: center; }

  .price-card {
    background: var(--paper);
    border: 2px solid var(--ink);
    border-radius: 16px;
    padding: 3.5rem;
    margin-top: 3rem;
    position: relative;
    box-shadow: 8px 8px 0 var(--ink);
    transition: transform .2s, box-shadow .2s;
  }
  .price-card:hover { transform: translate(-2px, -2px); box-shadow: 10px 10px 0 var(--ink); }

  .price-badge {
    position: absolute; top: -14px; left: 50%; transform: translateX(-50%);
    background: var(--gold); color: var(--ink);
    padding: 0.35rem 1.2rem; border-radius: 100px;
    font-size: 0.75rem; font-weight: 700; letter-spacing: 0.06em;
    text-transform: uppercase; white-space: nowrap;
  }
  .price-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem; font-weight: 700; margin-bottom: 0.5rem;
  }
  .price-amount {
    font-family: 'Playfair Display', serif;
    font-size: 4.5rem; font-weight: 900;
    line-height: 1; letter-spacing: -0.04em;
    color: var(--ink);
    margin: 1rem 0 0.3rem;
  }
  .price-amount sup { font-size: 2rem; vertical-align: top; margin-top: 0.7rem; display: inline-block; }
  .price-note { font-size: 0.85rem; color: var(--muted); margin-bottom: 2rem; }

  .price-features { list-style: none; text-align: left; margin-bottom: 2.5rem; }
  .price-features li {
    display: flex; align-items: center; gap: 0.8rem;
    padding: 0.7rem 0; border-bottom: 1px solid var(--border);
    font-size: 0.95rem;
  }
  .price-features li:last-child { border-bottom: none; }
  .check { color: var(--green); font-size: 1rem; flex-shrink: 0; }

  .btn-buy {
    display: block; width: 100%;
    background: var(--ink); color: var(--paper);
    padding: 1.1rem; border-radius: 8px;
    font-size: 1.05rem; font-weight: 700;
    text-decoration: none; text-align: center;
    transition: all .2s;
    letter-spacing: 0.01em;
  }
  .btn-buy:hover { background: var(--gold); color: var(--ink); }

  .guarantee {
    margin-top: 1.5rem;
    font-size: 0.82rem; color: var(--muted);
    display: flex; align-items: center; justify-content: center; gap: 0.4rem;
  }

  /* ── TESTIMONIALS ── */
  .testimonials { padding: 6rem 3rem; }
  .testi-inner { max-width: 1100px; margin: 0 auto; }
  .testi-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem; margin-top: 3rem;
  }
  .testi-card {
    background: var(--paper);
    border: 1.5px solid var(--border);
    border-radius: 10px; padding: 2rem;
    position: relative;
  }
  .testi-card::before {
    content: '"';
    position: absolute; top: 1rem; right: 1.5rem;
    font-family: 'Playfair Display', serif;
    font-size: 5rem; line-height: 1;
    color: var(--gold-light);
  }
  .stars { color: var(--gold); font-size: 0.9rem; margin-bottom: 0.8rem; letter-spacing: 2px; }
  .testi-text { font-size: 0.95rem; color: var(--ink); line-height: 1.7; margin-bottom: 1.2rem; font-style: italic; }
  .testi-author { font-size: 0.82rem; font-weight: 600; color: var(--muted); }

  /* ── FAQ ── */
  .faq-section { padding: 6rem 3rem; background: var(--cream); }
  .faq-inner { max-width: 720px; margin: 0 auto; }
  .faq-list { margin-top: 3rem; }
  .faq-item { border-bottom: 1.5px solid var(--border); }
  .faq-q {
    width: 100%; background: none; border: none; cursor: pointer;
    display: flex; justify-content: space-between; align-items: center;
    padding: 1.2rem 0;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.95rem; font-weight: 600; color: var(--ink);
    text-align: left; gap: 1rem;
  }
  .faq-q .arrow { transition: transform .3s; font-size: 0.9rem; color: var(--gold); flex-shrink: 0; }
  .faq-q.open .arrow { transform: rotate(180deg); }
  .faq-a {
    font-size: 0.9rem; color: var(--muted); line-height: 1.7;
    max-height: 0; overflow: hidden; transition: max-height .35s ease, padding .3s;
  }
  .faq-a.open { max-height: 300px; padding-bottom: 1.2rem; }

  /* ── FOOTER ── */
  footer {
    background: var(--ink); color: rgba(245,240,232,0.5);
    padding: 3rem;
    display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;
  }
  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem; font-weight: 700;
    color: var(--paper); text-decoration: none;
  }
  .footer-logo span { color: var(--gold); }
  footer p { font-size: 0.82rem; }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes underlineGrow {
    to { transform: scaleX(1); }
  }

  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .hero { padding: 7rem 1.5rem 3rem; }
    .section, .inside-section, .pricing-section, .testimonials, .faq-section { padding: 4rem 1.5rem; }
    .preview-section { padding: 1rem 1.5rem 4rem; }
    footer { flex-direction: column; text-align: center; padding: 2rem 1.5rem; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Finance<span>Flow</span> Pro</a>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#inside">What's Inside</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="#pricing" class="nav-cta">Get It Now →</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-inner">
    <div class="hero-badge">Excel Spreadsheet Template</div>
    <h1 class="hero-h1">
      Stop guessing.<br>Start <em>knowing</em><br>your money.
    </h1>
    <p class="hero-sub">
      A beautifully designed Excel tracker with income logging, expense management, profit calculation, and savings goal tracking — all in one file.
    </p>
    <div class="hero-actions">
      <a href="#pricing" class="btn-primary">Get Instant Access →</a>
      <a href="#inside" class="btn-secondary">See What's Inside</a>
    </div>
    <div class="hero-proof">
      <div class="proof-item"><span class="icon">✓</span> Instant download</div>
      <div class="proof-item"><span class="icon">✓</span> Works in Excel & Google Sheets</div>
      <div class="proof-item"><span class="icon">✓</span> No experience needed</div>
      <div class="proof-item"><span class="icon">✓</span> One-time purchase</div>
    </div>
  </div>
</section>

<!-- SPREADSHEET PREVIEW -->
<div class="preview-section">
  <div class="preview-wrapper reveal">
    <div class="preview-topbar">
      <div class="dot dot-r"></div>
      <div class="dot dot-y"></div>
      <div class="dot dot-g"></div>
      <span class="preview-filename">Personal_Finance_Tracker.xlsx</span>
    </div>
    <div class="preview-tabs">
      <div class="tab active">📊 Dashboard</div>
      <div class="tab">💰 Income</div>
      <div class="tab">💸 Expenses</div>
      <div class="tab">📈 Profit</div>
      <div class="tab">🎯 Goals</div>
    </div>
    <div class="spreadsheet-grid">
      <div class="sheet-header-row">
        <div class="sh-cell"></div>
        <div class="sh-cell">B</div>
        <div class="sh-cell">C</div>
        <div class="sh-cell">D</div>
        <div class="sh-cell">E</div>
        <div class="sh-cell">F</div>
      </div>
      <div class
