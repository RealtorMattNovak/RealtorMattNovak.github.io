<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Matthew Novak | Northgroup Real Estate</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #b8955a;
    --gold-light: #d4b07a;
    --dark: #0e0e0e;
    --dark-2: #1a1a1a;
    --dark-3: #242424;
    --mid: #3a3a3a;
    --light-gray: #8a8a8a;
    --off-white: #f5f2ee;
    --white: #ffffff;
    --serif: 'Cormorant Garamond', Georgia, serif;
    --sans: 'Montserrat', sans-serif;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: var(--sans);
    background: var(--dark);
    color: var(--white);
    overflow-x: hidden;
  }

  /* ── TOPBAR ── */
  #topbar {
    background: var(--dark);
    padding: 8px 40px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 24px;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    font-size: 11px;
    letter-spacing: 0.12em;
    color: var(--light-gray);
  }
  #topbar a { color: var(--light-gray); text-decoration: none; transition: color 0.2s; }
  #topbar a:hover { color: var(--gold); }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    background: transparent;
    transition: background 0.4s, padding 0.3s;
  }
  nav.scrolled {
    background: rgba(14,14,14,0.97);
    backdrop-filter: blur(12px);
    box-shadow: 0 2px 30px rgba(0,0,0,0.5);
  }
  .nav-inner {
    max-width: 1400px;
    margin: 0 auto;
    padding: 22px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .nav-logo {
    display: flex;
    flex-direction: column;
    line-height: 1;
    text-decoration: none;
  }
  .nav-logo .logo-name {
    font-family: var(--serif);
    font-size: 26px;
    font-weight: 500;
    color: var(--white);
    letter-spacing: 0.04em;
  }
  .nav-logo .logo-sub {
    font-size: 9px;
    letter-spacing: 0.28em;
    color: var(--gold);
    text-transform: uppercase;
    margin-top: 4px;
    font-weight: 600;
  }
  .nav-links {
    display: flex;
    list-style: none;
    gap: 32px;
    align-items: center;
  }
  .nav-links > li { position: relative; }
  .nav-links a {
    font-size: 11px;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.85);
    text-decoration: none;
    font-weight: 500;
    transition: color 0.2s;
    padding-bottom: 4px;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -2px; left: 0; right: 0;
    height: 1px;
    background: var(--gold);
    transform: scaleX(0);
    transition: transform 0.25s ease;
  }
  .nav-links a:hover::after { transform: scaleX(1); }

  /* Dropdown */
  .dropdown { position: relative; }
  .dropdown-menu {
    position: absolute;
    top: calc(100% + 16px);
    left: 50%;
    transform: translateX(-50%);
    background: rgba(14,14,14,0.97);
    border: 1px solid rgba(184,149,90,0.2);
    min-width: 200px;
    padding: 12px 0;
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.2s, transform 0.2s;
    transform: translateX(-50%) translateY(-6px);
  }
  .dropdown:hover .dropdown-menu {
    opacity: 1;
    visibility: visible;
    transform: translateX(-50%) translateY(0);
  }
  .dropdown-menu a {
    display: block;
    padding: 10px 20px;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: rgba(255,255,255,0.75) !important;
    white-space: nowrap;
  }
  .dropdown-menu a::after { display: none; }
  .dropdown-menu a:hover { color: var(--gold) !important; background: rgba(184,149,90,0.05); }

  .nav-cta {
    background: var(--gold);
    color: var(--dark) !important;
    padding: 10px 22px !important;
    font-weight: 600 !important;
    letter-spacing: 0.14em !important;
    transition: background 0.2s !important;
  }
  .nav-cta::after { display: none !important; }
  .nav-cta:hover { background: var(--gold-light) !important; color: var(--dark) !important; }

  /* Hamburger */
  .hamburger {
    display: none;
    flex-direction: column;
    gap: 5px;
    cursor: pointer;
    padding: 4px;
  }
  .hamburger span {
    width: 26px;
    height: 1.5px;
    background: var(--white);
    transition: all 0.3s;
  }

  /* Mobile menu */
  .mobile-menu {
    display: none;
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: var(--dark);
    z-index: 999;
    padding: 80px 40px 40px;
    flex-direction: column;
    gap: 0;
    overflow-y: auto;
  }
  .mobile-menu.open { display: flex; }
  .mobile-menu a {
    font-size: 13px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.8);
    text-decoration: none;
    padding: 16px 0;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    font-weight: 500;
  }
  .mobile-menu a:hover { color: var(--gold); }
  .mobile-close {
    position: absolute;
    top: 24px; right: 32px;
    font-size: 28px;
    color: var(--white);
    cursor: pointer;
    background: none;
    border: none;
    line-height: 1;
  }

  /* ── HERO ── */
  #hero {
    position: relative;
    height: 100vh;
    min-height: 700px;
    display: flex;
    align-items: flex-end;
    overflow: hidden;
  }
  .hero-slides { position: absolute; inset: 0; }
  .hero-slide {
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 1.2s ease;
    background-size: cover;
    background-position: center;
  }
  .hero-slide.active { opacity: 1; }
  /* Using Unsplash free luxury home images */
  .hero-slide:nth-child(1) { background-image: url('https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=1800&auto=format&fit=crop&q=80'); }
  .hero-slide:nth-child(2) { background-image: url('https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=1800&auto=format&fit=crop&q=80'); }
  .hero-slide:nth-child(3) { background-image: url('https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=1800&auto=format&fit=crop&q=80'); }
  .hero-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to top,
      rgba(14,14,14,0.92) 0%,
      rgba(14,14,14,0.4) 50%,
      rgba(14,14,14,0.15) 100%
    );
  }
  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 1400px;
    width: 100%;
    margin: 0 auto;
    padding: 0 40px 80px;
  }
  .hero-eyebrow {
    font-size: 10px;
    letter-spacing: 0.32em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 18px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.3s forwards;
  }
  .hero-title {
    font-family: var(--serif);
    font-size: clamp(52px, 7vw, 96px);
    font-weight: 300;
    line-height: 1.0;
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.5s forwards;
  }
  .hero-title em {
    font-style: italic;
    color: var(--gold-light);
  }
  .hero-subtitle {
    font-size: 13px;
    letter-spacing: 0.1em;
    color: rgba(255,255,255,0.65);
    max-width: 480px;
    line-height: 1.8;
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.7s forwards;
    font-weight: 300;
  }
  .hero-btns {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.9s forwards;
  }
  .btn-primary {
    background: var(--gold);
    color: var(--dark);
    padding: 15px 36px;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 700;
    text-decoration: none;
    transition: background 0.2s, transform 0.2s;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-1px); }
  .btn-outline {
    border: 1px solid rgba(255,255,255,0.4);
    color: var(--white);
    padding: 15px 36px;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 600;
    text-decoration: none;
    transition: border-color 0.2s, transform 0.2s;
  }
  .btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-1px); }

  /* Slide dots */
  .hero-dots {
    position: absolute;
    bottom: 36px;
    right: 40px;
    z-index: 3;
    display: flex;
    gap: 8px;
  }
  .hero-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: rgba(255,255,255,0.3);
    cursor: pointer;
    transition: background 0.3s;
    border: none;
  }
  .hero-dot.active { background: var(--gold); width: 22px; border-radius: 3px; }

  /* Scroll indicator */
  .scroll-indicator {
    position: absolute;
    bottom: 36px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 3;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    color: rgba(255,255,255,0.4);
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }
  .scroll-line {
    width: 1px;
    height: 40px;
    background: rgba(255,255,255,0.2);
    animation: scrollPulse 2s ease infinite;
  }
  @keyframes scrollPulse {
    0%,100% { opacity: 0.3; transform: scaleY(1); }
    50% { opacity: 1; transform: scaleY(0.6); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── STATS BAR ── */
  #stats {
    background: var(--gold);
    padding: 28px 40px;
  }
  .stats-inner {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    divide-x: 1px solid rgba(0,0,0,0.15);
  }
  .stat-item {
    text-align: center;
    padding: 0 20px;
    border-right: 1px solid rgba(0,0,0,0.15);
  }
  .stat-item:last-child { border-right: none; }
  .stat-num {
    font-family: var(--serif);
    font-size: 36px;
    font-weight: 600;
    color: var(--dark);
    line-height: 1;
  }
  .stat-label {
    font-size: 9px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: rgba(0,0,0,0.6);
    font-weight: 600;
    margin-top: 6px;
  }

  /* ── SEARCH ── */
  #search {
    background: var(--dark-2);
    padding: 60px 40px;
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
  .search-inner {
    max-width: 900px;
    margin: 0 auto;
    text-align: center;
  }
  .search-label {
    font-size: 10px;
    letter-spacing: 0.3em;
    color: var(--gold);
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: 14px;
  }
  .search-title {
    font-family: var(--serif);
    font-size: 38px;
    font-weight: 300;
    margin-bottom: 32px;
    color: var(--white);
  }
  .search-form {
    display: flex;
    gap: 0;
    max-width: 700px;
    margin: 0 auto 20px;
  }
  .search-form input {
    flex: 1;
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    border-right: none;
    color: var(--white);
    padding: 16px 24px;
    font-family: var(--sans);
    font-size: 13px;
    outline: none;
    letter-spacing: 0.05em;
  }
  .search-form input::placeholder { color: rgba(255,255,255,0.3); }
  .search-form input:focus { border-color: var(--gold); background: rgba(184,149,90,0.05); }
  .search-form button {
    background: var(--gold);
    border: none;
    color: var(--dark);
    padding: 16px 32px;
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s;
  }
  .search-form button:hover { background: var(--gold-light); }
  .search-tabs {
    display: flex;
    justify-content: center;
    gap: 0;
    border: 1px solid rgba(255,255,255,0.1);
    max-width: 400px;
    margin: 0 auto;
  }
  .search-tab {
    flex: 1;
    padding: 10px 20px;
    font-size: 10px;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.5);
    cursor: pointer;
    border: none;
    background: transparent;
    font-family: var(--sans);
    font-weight: 600;
    transition: all 0.2s;
    border-right: 1px solid rgba(255,255,255,0.1);
  }
  .search-tab:last-child { border-right: none; }
  .search-tab.active, .search-tab:hover { background: var(--gold); color: var(--dark); }

  /* ── SECTION COMMONS ── */
  .section-label {
    font-size: 10px;
    letter-spacing: 0.3em;
    color: var(--gold);
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: 12px;
  }
  .section-title {
    font-family: var(--serif);
    font-size: clamp(34px, 4vw, 54px);
    font-weight: 300;
    line-height: 1.1;
  }
  .section-title em { font-style: italic; color: var(--gold-light); }

  /* ── LISTINGS ── */
  #listings {
    padding: 100px 40px;
    background: var(--dark);
  }
  .listings-header {
    max-width: 1400px;
    margin: 0 auto 56px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
  }
  .view-all {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    text-decoration: none;
    font-weight: 600;
    border-bottom: 1px solid var(--gold);
    padding-bottom: 2px;
    transition: color 0.2s;
  }
  .view-all:hover { color: var(--gold-light); border-color: var(--gold-light); }
  .listings-grid {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }
  .listing-card {
    position: relative;
    overflow: hidden;
    cursor: pointer;
    background: var(--dark-3);
  }
  .listing-card:first-child {
    grid-column: span 2;
    grid-row: span 1;
  }
  .listing-img {
    width: 100%;
    aspect-ratio: 4/3;
    object-fit: cover;
    display: block;
    transition: transform 0.6s ease;
    filter: brightness(0.85);
  }
  .listing-card:first-child .listing-img { aspect-ratio: 16/9; }
  .listing-card:hover .listing-img { transform: scale(1.05); filter: brightness(0.7); }
  .listing-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(14,14,14,0.9) 0%, transparent 60%);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 28px;
    transition: background 0.3s;
  }
  .listing-tag {
    position: absolute;
    top: 18px; left: 18px;
    background: var(--gold);
    color: var(--dark);
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 700;
    padding: 5px 12px;
  }
  .listing-price {
    font-family: var(--serif);
    font-size: 26px;
    font-weight: 500;
    color: var(--white);
    line-height: 1;
    margin-bottom: 6px;
  }
  .listing-card:first-child .listing-price { font-size: 36px; }
  .listing-address {
    font-size: 11px;
    letter-spacing: 0.08em;
    color: rgba(255,255,255,0.75);
    margin-bottom: 10px;
  }
  .listing-meta {
    display: flex;
    gap: 16px;
    font-size: 10px;
    letter-spacing: 0.1em;
    color: rgba(255,255,255,0.5);
    text-transform: uppercase;
  }

  /* ── ABOUT ── */
  #about {
    padding: 120px 40px;
    background: var(--dark-2);
  }
  .about-inner {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 100px;
    align-items: center;
  }
  .about-img-wrap {
    position: relative;
  }
  .about-img {
    width: 100%;
    aspect-ratio: 3/4;
    object-fit: cover;
    display: block;
    filter: grayscale(15%);
  }
  .about-img-accent {
    position: absolute;
    bottom: -24px;
    right: -24px;
    width: 60%;
    height: 60%;
    border: 2px solid var(--gold);
    z-index: -1;
  }
  .about-img-badge {
    position: absolute;
    bottom: 32px;
    left: -32px;
    background: var(--gold);
    color: var(--dark);
    padding: 20px 24px;
    text-align: center;
  }
  .badge-num {
    font-family: var(--serif);
    font-size: 42px;
    font-weight: 600;
    line-height: 1;
  }
  .badge-text {
    font-size: 8px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    font-weight: 700;
    margin-top: 4px;
  }
  .about-content { padding-right: 20px; }
  .about-content .section-label { margin-bottom: 10px; }
  .about-content .section-title { margin-bottom: 28px; }
  .about-text {
    font-size: 15px;
    line-height: 1.9;
    color: rgba(255,255,255,0.65);
    margin-bottom: 20px;
    font-weight: 300;
  }
  .about-highlights {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
    margin: 36px 0;
  }
  .highlight-item {
    border-left: 2px solid var(--gold);
    padding-left: 16px;
  }
  .highlight-num {
    font-family: var(--serif);
    font-size: 28px;
    font-weight: 500;
    color: var(--gold);
  }
  .highlight-label {
    font-size: 9px;
    letter-spacing: 0.18em;
    color: rgba(255,255,255,0.45);
    text-transform: uppercase;
    font-weight: 600;
    margin-top: 3px;
  }

  /* ── SERVICES ── */
  #services {
    padding: 100px 40px;
    background: var(--dark);
  }
  .services-inner {
    max-width: 1400px;
    margin: 0 auto;
  }
  .services-header {
    text-align: center;
    margin-bottom: 64px;
  }
  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }
  .service-card {
    background: var(--dark-3);
    padding: 52px 44px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .service-card:hover { background: var(--dark-2); }
  .service-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 100%; height: 2px;
    background: var(--gold);
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }
  .service-card:hover::before { transform: scaleX(1); }
  .service-icon {
    width: 44px;
    height: 44px;
    border: 1px solid var(--gold);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 28px;
    color: var(--gold);
    font-size: 18px;
  }
  .service-title {
    font-family: var(--serif);
    font-size: 26px;
    font-weight: 400;
    margin-bottom: 16px;
    color: var(--white);
  }
  .service-text {
    font-size: 13px;
    line-height: 1.85;
    color: rgba(255,255,255,0.5);
    font-weight: 300;
  }
  .service-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    margin-top: 24px;
    font-size: 10px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--gold);
    text-decoration: none;
    font-weight: 600;
    transition: gap 0.2s;
  }
  .service-link:hover { gap: 14px; }

  /* ── TESTIMONIALS ── */
  #testimonials {
    padding: 120px 40px;
    background: var(--dark-2);
    position: relative;
    overflow: hidden;
  }
  #testimonials::before {
    content: '"';
    position: absolute;
    top: -40px;
    left: 50%;
    transform: translateX(-50%);
    font-family: var(--serif);
    font-size: 400px;
    color: rgba(184,149,90,0.04);
    line-height: 1;
    pointer-events: none;
  }
  .testimonials-inner {
    max-width: 900px;
    margin: 0 auto;
    text-align: center;
    position: relative;
    z-index: 1;
  }
  .testimonial-slider { position: relative; min-height: 200px; }
  .testimonial {
    display: none;
    animation: fadeIn 0.6s ease;
  }
  .testimonial.active { display: block; }
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  .testimonial-quote {
    font-family: var(--serif);
    font-size: clamp(20px, 2.5vw, 28px);
    font-weight: 300;
    font-style: italic;
    line-height: 1.6;
    color: rgba(255,255,255,0.85);
    margin-bottom: 36px;
  }
  .testimonial-author {
    font-size: 10px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
  }
  .testimonial-role {
    font-size: 11px;
    color: rgba(255,255,255,0.35);
    margin-top: 4px;
    letter-spacing: 0.06em;
  }
  .testimonial-nav {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-top: 48px;
  }
  .t-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: rgba(255,255,255,0.2);
    border: none;
    cursor: pointer;
    transition: all 0.3s;
  }
  .t-dot.active { background: var(--gold); width: 22px; border-radius: 3px; }
  .testimonial-arrows {
    display: flex;
    justify-content: center;
    gap: 16px;
    margin-top: 24px;
  }
  .t-arrow {
    width: 44px; height: 44px;
    border: 1px solid rgba(255,255,255,0.15);
    background: transparent;
    color: rgba(255,255,255,0.6);
    font-size: 16px;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .t-arrow:hover { border-color: var(--gold); color: var(--gold); }

  /* ── CTA BAND ── */
  #cta-band {
    padding: 0;
    background: var(--dark);
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
  .cta-item {
    padding: 60px 40px;
    text-align: center;
    border-right: 1px solid rgba(255,255,255,0.04);
    text-decoration: none;
    transition: background 0.3s;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 14px;
    color: var(--white);
  }
  .cta-item:last-child { border-right: none; }
  .cta-item:hover { background: var(--gold); color: var(--dark); }
  .cta-item:hover .cta-icon, .cta-item:hover .cta-label, .cta-item:hover .cta-sub { color: var(--dark); }
  .cta-icon { font-size: 28px; color: var(--gold); transition: color 0.3s; }
  .cta-label {
    font-family: var(--serif);
    font-size: 22px;
    font-weight: 400;
    transition: color 0.3s;
  }
  .cta-sub {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.4);
    font-weight: 600;
    transition: color 0.3s;
  }

  /* ── NEIGHBORHOODS ── */
  #neighborhoods {
    padding: 100px 40px;
    background: var(--dark-2);
  }
  .neighborhoods-inner { max-width: 1400px; margin: 0 auto; }
  .neighborhoods-header { margin-bottom: 56px; }
  .neighborhoods-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
  }
  .neighborhood-card {
    position: relative;
    overflow: hidden;
    cursor: pointer;
  }
  .neighborhood-img {
    width: 100%;
    aspect-ratio: 3/4;
    object-fit: cover;
    display: block;
    transition: transform 0.5s ease;
    filter: brightness(0.6);
  }
  .neighborhood-card:hover .neighborhood-img { transform: scale(1.06); filter: brightness(0.45); }
  .neighborhood-overlay {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 24px;
    background: linear-gradient(to top, rgba(14,14,14,0.75) 0%, transparent 60%);
  }
  .neighborhood-name {
    font-family: var(--serif);
    font-size: 22px;
    font-weight: 400;
    color: var(--white);
  }
  .neighborhood-count {
    font-size: 10px;
    letter-spacing: 0.14em;
    color: var(--gold);
    text-transform: uppercase;
    font-weight: 600;
    margin-top: 4px;
  }

  /* ── CONTACT ── */
  #contact {
    padding: 120px 40px;
    background: var(--dark);
  }
  .contact-inner {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 100px;
    align-items: start;
  }
  .contact-info .section-title { margin-bottom: 28px; }
  .contact-text {
    font-size: 15px;
    line-height: 1.9;
    color: rgba(255,255,255,0.55);
    font-weight: 300;
    margin-bottom: 44px;
  }
  .contact-details { display: flex; flex-direction: column; gap: 20px; }
  .contact-detail {
    display: flex;
    align-items: flex-start;
    gap: 16px;
  }
  .contact-detail-icon {
    width: 36px; height: 36px;
    border: 1px solid rgba(184,149,90,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--gold);
    font-size: 14px;
    flex-shrink: 0;
    margin-top: 2px;
  }
  .contact-detail-label {
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 4px;
  }
  .contact-detail-value {
    font-size: 14px;
    color: rgba(255,255,255,0.75);
    font-weight: 300;
    text-decoration: none;
    transition: color 0.2s;
  }
  a.contact-detail-value:hover { color: var(--gold); }
  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 18px;
  }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; }
  .form-group { display: flex; flex-direction: column; gap: 8px; }
  .form-label {
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.4);
    font-weight: 600;
  }
  .form-input, .form-select, .form-textarea {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    color: var(--white);
    padding: 14px 18px;
    font-family: var(--sans);
    font-size: 13px;
    outline: none;
    transition: border-color 0.2s;
    letter-spacing: 0.04em;
    font-weight: 300;
  }
  .form-select {
    appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23b8955a' stroke-width='1.5' fill='none'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 16px center;
  }
  .form-textarea { resize: vertical; min-height: 130px; }
  .form-input::placeholder, .form-textarea::placeholder { color: rgba(255,255,255,0.2); }
  .form-input:focus, .form-select:focus, .form-textarea:focus {
    border-color: var(--gold);
    background: rgba(184,149,90,0.04);
  }
  .form-select option { background: var(--dark-3); }
  .form-consent {
    font-size: 11px;
    color: rgba(255,255,255,0.3);
    line-height: 1.6;
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }
  .form-consent input { margin-top: 3px; accent-color: var(--gold); }
  .form-submit {
    background: var(--gold);
    border: none;
    color: var(--dark);
    padding: 18px 44px;
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s, transform 0.2s;
    align-self: flex-start;
  }
  .form-submit:hover { background: var(--gold-light); transform: translateY(-1px); }

  /* ── FOOTER ── */
  footer {
    background: var(--dark-3);
    border-top: 1px solid rgba(255,255,255,0.05);
    padding: 80px 40px 40px;
  }
  .footer-top {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px;
    margin-bottom: 60px;
    padding-bottom: 60px;
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
  .footer-brand .logo-name {
    font-family: var(--serif);
    font-size: 28px;
    font-weight: 500;
    color: var(--white);
    letter-spacing: 0.04em;
    display: block;
    margin-bottom: 4px;
    text-decoration: none;
  }
  .footer-brand .logo-sub {
    font-size: 9px;
    letter-spacing: 0.28em;
    color: var(--gold);
    text-transform: uppercase;
    font-weight: 600;
    display: block;
    margin-bottom: 20px;
  }
  .footer-brand-text {
    font-size: 13px;
    line-height: 1.8;
    color: rgba(255,255,255,0.35);
    font-weight: 300;
    max-width: 320px;
  }
  .footer-social {
    display: flex;
    gap: 12px;
    margin-top: 24px;
  }
  .social-link {
    width: 36px; height: 36px;
    border: 1px solid rgba(255,255,255,0.1);
    display: flex;
    align-items: center;
    justify-content: center;
    color: rgba(255,255,255,0.4);
    text-decoration: none;
    font-size: 14px;
    transition: all 0.2s;
  }
  .social-link:hover { border-color: var(--gold); color: var(--gold); }
  .footer-col-title {
    font-size: 9px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 700;
    margin-bottom: 20px;
  }
  .footer-links { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .footer-links a {
    font-size: 12px;
    color: rgba(255,255,255,0.4);
    text-decoration: none;
    letter-spacing: 0.05em;
    transition: color 0.2s;
    font-weight: 300;
  }
  .footer-links a:hover { color: var(--gold); }
  .footer-bottom {
    max-width: 1400px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
  }
  .footer-copy {
    font-size: 11px;
    color: rgba(255,255,255,0.2);
    letter-spacing: 0.06em;
  }
  .footer-legal { display: flex; gap: 24px; }
  .footer-legal a {
    font-size: 11px;
    color: rgba(255,255,255,0.2);
    text-decoration: none;
    letter-spacing: 0.06em;
    transition: color 0.2s;
  }
  .footer-legal a:hover { color: var(--gold); }

  /* ── NEWSLETTER STRIP ── */
  #newsletter {
    background: var(--gold);
    padding: 56px 40px;
  }
  .newsletter-inner {
    max-width: 1400px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    gap: 48px;
    justify-content: space-between;
  }
  .newsletter-text .section-label { color: var(--dark); opacity: 0.6; }
  .newsletter-text .section-title {
    font-size: 32px;
    color: var(--dark);
  }
  .newsletter-form {
    display: flex;
    gap: 0;
    flex: 1;
    max-width: 480px;
  }
  .newsletter-form input {
    flex: 1;
    background: rgba(0,0,0,0.12);
    border: 1px solid rgba(0,0,0,0.15);
    border-right: none;
    color: var(--dark);
    padding: 15px 20px;
    font-family: var(--sans);
    font-size: 13px;
    outline: none;
  }
  .newsletter-form input::placeholder { color: rgba(0,0,0,0.4); }
  .newsletter-form button {
    background: var(--dark);
    color: var(--white);
    border: none;
    padding: 15px 28px;
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s;
  }
  .newsletter-form button:hover { background: var(--dark-3); }

  /* ── RESPONSIVE ── */
  @media (max-width: 1100px) {
    .listings-grid { grid-template-columns: 1fr 1fr; }
    .listing-card:first-child { grid-column: span 2; }
    .services-grid { grid-template-columns: 1fr 1fr; }
    .neighborhoods-grid { grid-template-columns: repeat(2, 1fr); }
    .footer-top { grid-template-columns: 1fr 1fr; gap: 40px; }
    #cta-band { grid-template-columns: repeat(2, 1fr); }
    .stats-inner { grid-template-columns: repeat(2, 1fr); gap: 0; }
    .stat-item { padding: 20px; border-bottom: 1px solid rgba(0,0,0,0.1); }
    .newsletter-inner { flex-direction: column; gap: 28px; }
    .newsletter-form { max-width: 100%; width: 100%; }
  }

  @media (max-width: 768px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .nav-inner { padding: 18px 20px; }
    #topbar { display: none; }
    .hero-content { padding: 0 20px 60px; }
    .about-inner { grid-template-columns: 1fr; gap: 60px; }
    .contact-inner { grid-template-columns: 1fr; gap: 60px; }
    .listings-grid { grid-template-columns: 1fr; }
    .listing-card:first-child { grid-column: auto; }
    .services-grid { grid-template-columns: 1fr; }
    .neighborhoods-grid { grid-template-columns: repeat(2, 1fr); }
    #cta-band { grid-template-columns: repeat(2, 1fr); }
    #stats { padding: 28px 20px; }
    .stats-inner { grid-template-columns: repeat(2, 1fr); }
    #listings, #about, #services, #testimonials, #contact { padding: 70px 20px; }
    #neighborhoods { padding: 70px 20px; }
    .footer-top { grid-template-columns: 1fr; gap: 32px; }
    .footer-bottom { flex-direction: column; text-align: center; }
    .form-row { grid-template-columns: 1fr; }
    .about-img-badge { left: 16px; bottom: 16px; }
    #newsletter { padding: 48px 20px; }
    .listings-header { flex-direction: column; align-items: flex-start; gap: 16px; }
  }
</style>
</head>
<body>

<!-- TOPBAR -->
<div id="topbar">
  <a href="tel:+17045550100">(704) 555-0100</a>
  <span>|</span>
  <a href="mailto:matthew@northgroupre.com">matthew@northgroupre.com</a>
</div>

<!-- NAV -->
<nav id="main-nav">
  <div class="nav-inner">
    <a href="#" class="nav-logo">
      <span class="logo-name">Matthew Novak</span>
      <span class="logo-sub">Northgroup Real Estate</span>
    </a>
    <ul class="nav-links">
      <li class="dropdown">
        <a href="#listings">Properties ▾</a>
        <div class="dropdown-menu">
          <a href="#listings">Active Listings</a>
          <a href="#listings">Open Houses</a>
          <a href="#listings">Recent Sales</a>
        </div>
      </li>
      <li><a href="#about">About</a></li>
      <li class="dropdown">
        <a href="#services">Services ▾</a>
        <div class="dropdown-menu">
          <a href="#services">Buy With Me</a>
          <a href="#services">List With Me</a>
          <a href="#services">Home Valuation</a>
        </div>
      </li>
      <li><a href="#neighborhoods">Neighborhoods</a></li>
      <li><a href="#testimonials">Reviews</a></li>
      <li><a href="#contact" class="nav-cta">Contact</a></li>
    </ul>
    <div class="hamburger" id="hamburger" onclick="toggleMobileMenu()">
      <span></span><span></span><span></span>
    </div>
  </div>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobile-menu">
  <button class="mobile-close" onclick="toggleMobileMenu()">✕</button>
  <a href="#listings" onclick="toggleMobileMenu()">Properties</a>
  <a href="#about" onclick="toggleMobileMenu()">About</a>
  <a href="#services" onclick="toggleMobileMenu()">Services</a>
  <a href="#neighborhoods" onclick="toggleMobileMenu()">Neighborhoods</a>
  <a href="#testimonials" onclick="toggleMobileMenu()">Reviews</a>
  <a href="#contact" onclick="toggleMobileMenu()">Contact</a>
</div>

<!-- HERO -->
<section id="hero">
  <div class="hero-slides">
    <div class="hero-slide active"></div>
    <div class="hero-slide"></div>
    <div class="hero-slide"></div>
  </div>
  <div class="hero-overlay"></div>
  <div class="hero-content">
    <p class="hero-eyebrow">Northgroup Real Estate · Charlotte & Beyond</p>
    <h1 class="hero-title">Find Your <em>Perfect</em><br>Home in the<br>Carolinas</h1>
    <p class="hero-subtitle">With deep roots in the Charlotte market and a relentless commitment to exceptional service, Matthew Novak delivers results that speak for themselves.</p>
    <div class="hero-btns">
      <a href="#listings" class="btn-primary">View Listings</a>
      <a href="#contact" class="btn-outline">Get in Touch</a>
    </div>
  </div>
  <div class="hero-dots">
    <button class="hero-dot active" onclick="goToSlide(0)"></button>
    <button class="hero-dot" onclick="goToSlide(1)"></button>
    <button class="hero-dot" onclick="goToSlide(2)"></button>
  </div>
  <div class="scroll-indicator">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<!-- STATS BAR -->
<div id="stats">
  <div class="stats-inner">
    <div class="stat-item">
      <div class="stat-num">$120M+</div>
      <div class="stat-label">Total Sales Volume</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">350+</div>
      <div class="stat-label">Homes Sold</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">15+</div>
      <div class="stat-label">Years Experience</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">98%</div>
      <div class="stat-label">Client Satisfaction</div>
    </div>
  </div>
</div>

<!-- SEARCH -->
<div id="search">
  <div class="search-inner">
    <p class="search-label">Search Properties</p>
    <h2 class="search-title">Find Your Dream Home</h2>
    <div class="search-tabs" style="margin-bottom:24px;">
      <button class="search-tab active" onclick="setTab(this)">Buy</button>
      <button class="search-tab" onclick="setTab(this)">Rent</button>
      <button class="search-tab" onclick="setTab(this)">Sold</button>
    </div>
    <div class="search-form">
      <input type="text" placeholder="City, ZIP, neighborhood, or address…">
      <button>Search</button>
    </div>
  </div>
</div>

<!-- LISTINGS -->
<section id="listings">
  <div class="listings-header">
    <div>
      <p class="section-label">Featured Properties</p>
      <h2 class="section-title">Exclusive <em>Listings</em></h2>
    </div>
    <a href="#" class="view-all">View All Properties →</a>
  </div>
  <div class="listings-grid">

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1580587771525-78b9dba3b914?w=1200&auto=format&fit=crop&q=80"
        alt="4201 Providence Rd">
      <div class="listing-overlay">
        <span class="listing-tag">Featured</span>
        <div class="listing-price">$1,850,000</div>
        <div class="listing-address">4201 Providence Rd, Charlotte, NC 28211</div>
        <div class="listing-meta"><span>5 Beds</span><span>/</span><span>4.5 Baths</span><span>/</span><span>5,200 sqft</span></div>
      </div>
    </div>

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?w=800&auto=format&fit=crop&q=80"
        alt="1540 Dilworth Rd">
      <div class="listing-overlay">
        <span class="listing-tag">New</span>
        <div class="listing-price">$975,000</div>
        <div class="listing-address">1540 Dilworth Rd, Charlotte, NC 28203</div>
        <div class="listing-meta"><span>4 Beds</span><span>/</span><span>3 Baths</span><span>/</span><span>3,100 sqft</span></div>
      </div>
    </div>

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1600607688969-a5bfcd646154?w=800&auto=format&fit=crop&q=80"
        alt="310 Selwyn Ave">
      <div class="listing-overlay">
        <div class="listing-price">$1,250,000</div>
        <div class="listing-address">310 Selwyn Ave, Charlotte, NC 28209</div>
        <div class="listing-meta"><span>4 Beds</span><span>/</span><span>3.5 Baths</span><span>/</span><span>3,800 sqft</span></div>
      </div>
    </div>

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1523217582562-09d0def993a6?w=800&auto=format&fit=crop&q=80"
        alt="8720 Birkdale Crossing">
      <div class="listing-overlay">
        <span class="listing-tag">Open House</span>
        <div class="listing-price">$750,000</div>
        <div class="listing-address">8720 Birkdale Crossing, Huntersville, NC 28078</div>
        <div class="listing-meta"><span>3 Beds</span><span>/</span><span>2.5 Baths</span><span>/</span><span>2,800 sqft</span></div>
      </div>
    </div>

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1564013799919-ab600027ffc6?w=800&auto=format&fit=crop&q=80"
        alt="1102 Queens Rd W">
      <div class="listing-overlay">
        <div class="listing-price">$2,100,000</div>
        <div class="listing-address">1102 Queens Rd W, Charlotte, NC 28207</div>
        <div class="listing-meta"><span>6 Beds</span><span>/</span><span>5 Baths</span><span>/</span><span>6,400 sqft</span></div>
      </div>
    </div>

    <div class="listing-card">
      <img class="listing-img"
        src="https://images.unsplash.com/photo-1554995207-c18c203602cb?w=800&auto=format&fit=crop&q=80"
        alt="423 Olmsted Park Pl">
      <div class="listing-overlay">
        <span class="listing-tag">Price Reduced</span>
        <div class="listing-price">$589,000</div>
        <div class="listing-address">423 Olmsted Park Pl, Charlotte, NC 28209</div>
        <div class="listing-meta"><span>3 Beds</span><span>/</span><span>2 Baths</span><span>/</span><span>2,100 sqft</span></div>
      </div>
    </div>

  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-inner">
    <div class="about-img-wrap">
      <img class="about-img"
        src="https://images.unsplash.com/photo-1560250097-0b93528c311a?w=800&auto=format&fit=crop&q=80"
        alt="Matthew Novak">
      <div class="about-img-accent"></div>
      <div class="about-img-badge">
        <div class="badge-num">15+</div>
        <div class="badge-text">Years in<br>Charlotte</div>
      </div>
    </div>
    <div class="about-content">
      <p class="section-label">About Matthew</p>
      <h2 class="section-title">Your Trusted<br><em>Charlotte</em> Expert</h2>
      <p class="about-text">
        As one of Charlotte's top-producing agents at Northgroup Real Estate, Matthew Novak brings a rare combination of market expertise, negotiating skill, and genuine care for his clients to every transaction.
      </p>
      <p class="about-text">
        Whether you're searching for your first home in NoDa, upgrading to a Myers Park estate, or looking to invest in the Ballantyne corridor, Matthew provides the insight and strategy to help you succeed in any market.
      </p>
      <div class="about-highlights">
        <div class="highlight-item">
          <div class="highlight-num">$120M+</div>
          <div class="highlight-label">Total Volume Closed</div>
        </div>
        <div class="highlight-item">
          <div class="highlight-num">350+</div>
          <div class="highlight-label">Homes Sold</div>
        </div>
        <div class="highlight-item">
          <div class="highlight-num">Top 1%</div>
          <div class="highlight-label">Charlotte Agents</div>
        </div>
        <div class="highlight-item">
          <div class="highlight-num">5★</div>
          <div class="highlight-label">Average Rating</div>
        </div>
      </div>
      <a href="#contact" class="btn-primary">Work With Matthew</a>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="services-inner">
    <div class="services-header">
      <p class="section-label">What I Offer</p>
      <h2 class="section-title">Full-Service <em>Real Estate</em></h2>
    </div>
    <div class="services-grid">
      <div class="service-card">
        <div class="service-icon">⌂</div>
        <div class="service-title">Buyer Representation</div>
        <p class="service-text">From your first showing to closing day, I guide you through every step — search strategy, offer writing, inspections, and negotiations — ensuring you purchase at the right price.</p>
        <a href="#contact" class="service-link">Learn More →</a>
      </div>
      <div class="service-card">
        <div class="service-icon">◈</div>
        <div class="service-title">Seller Marketing</div>
        <p class="service-text">Professional photography, targeted digital campaigns, and a curated network of buyers help your property stand out — consistently achieving above-ask results.</p>
        <a href="#contact" class="service-link">Learn More →</a>
      </div>
      <div class="service-card">
        <div class="service-icon">◎</div>
        <div class="service-title">Home Valuation</div>
        <p class="service-text">Receive a complimentary, data-driven market analysis of your home's current value, backed by the latest Charlotte MLS data and neighborhood trends.</p>
        <a href="#contact" class="service-link">Get My Valuation →</a>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="testimonials-inner">
    <p class="section-label" style="margin-bottom:12px;">Client Reviews</p>
    <h2 class="section-title" style="margin-bottom:56px;">What Clients <em>Are Saying</em></h2>
    <div class="testimonial-slider">
      <div class="testimonial active">
        <p class="testimonial-quote">"Matthew went above and beyond to find us our dream home in Myers Park. His knowledge of the Charlotte market is unmatched — we were under contract in 48 hours at $30k under asking."</p>
        <div class="testimonial-author">Sarah & James T.</div>
        <div class="testimonial-role">Buyers — Myers Park, Charlotte</div>
      </div>
      <div class="testimonial">
        <p class="testimonial-quote">"Selling our Dilworth home was seamless. Matthew's marketing strategy generated 11 offers in the first weekend, and we closed at 106% of list price. Truly exceptional."</p>
        <div class="testimonial-author">Rebecca M.</div>
        <div class="testimonial-role">Seller — Dilworth, Charlotte</div>
      </div>
      <div class="testimonial">
        <p class="testimonial-quote">"As first-time buyers, we were nervous about the process. Matthew was patient, thorough, and always available. We couldn't imagine navigating the Charlotte market without him."</p>
        <div class="testimonial-author">David & Priya K.</div>
        <div class="testimonial-role">First-Time Buyers — NoDa, Charlotte</div>
      </div>
      <div class="testimonial">
        <p class="testimonial-quote">"Matthew's expertise in the Ballantyne area is remarkable. He helped us find an off-market listing that perfectly fit our needs. Highly recommend to anyone looking in south Charlotte."</p>
        <div class="testimonial-author">Michael F.</div>
        <div class="testimonial-role">Buyer — Ballantyne, Charlotte</div>
      </div>
    </div>
    <div class="testimonial-arrows">
      <button class="t-arrow" onclick="prevTestimonial()">←</button>
      <button class="t-arrow" onclick="nextTestimonial()">→</button>
    </div>
    <div class="testimonial-nav" id="t-dots"></div>
  </div>
</section>

<!-- CTA BAND -->
<div id="cta-band">
  <a href="#listings" class="cta-item">
    <div class="cta-icon">⌂</div>
    <div class="cta-label">Browse Homes</div>
    <div class="cta-sub">Active Listings</div>
  </a>
  <a href="#contact" class="cta-item">
    <div class="cta-icon">◎</div>
    <div class="cta-label">Home Value</div>
    <div class="cta-sub">Free Estimate</div>
  </a>
  <a href="#contact" class="cta-item">
    <div class="cta-icon">◈</div>
    <div class="cta-label">Sell With Me</div>
    <div class="cta-sub">Listing Services</div>
  </a>
  <a href="#neighborhoods" class="cta-item">
    <div class="cta-icon">⊕</div>
    <div class="cta-label">Explore Areas</div>
    <div class="cta-sub">Neighborhood Guides</div>
  </a>
</div>

<!-- NEIGHBORHOODS -->
<section id="neighborhoods">
  <div class="neighborhoods-inner">
    <div class="neighborhoods-header">
      <p class="section-label">Local Expertise</p>
      <h2 class="section-title">Charlotte <em>Neighborhoods</em></h2>
    </div>
    <div class="neighborhoods-grid">
      <div class="neighborhood-card">
        <img class="neighborhood-img"
          src="https://images.unsplash.com/photo-1449844908441-8829872d2607?w=600&auto=format&fit=crop&q=80"
          alt="Myers Park">
        <div class="neighborhood-overlay">
          <div class="neighborhood-name">Myers Park</div>
          <div class="neighborhood-count">12 Listings</div>
        </div>
      </div>
      <div class="neighborhood-card">
        <img class="neighborhood-img"
          src="https://images.unsplash.com/photo-1465301055284-72f355d86ba0?w=600&auto=format&fit=crop&q=80"
          alt="Dilworth">
        <div class="neighborhood-overlay">
          <div class="neighborhood-name">Dilworth</div>
          <div class="neighborhood-count">8 Listings</div>
        </div>
      </div>
      <div class="neighborhood-card">
        <img class="neighborhood-img"
          src="https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?w=600&auto=format&fit=crop&q=80"
          alt="Ballantyne">
        <div class="neighborhood-overlay">
          <div class="neighborhood-name">Ballantyne</div>
          <div class="neighborhood-count">17 Listings</div>
        </div>
      </div>
      <div class="neighborhood-card">
        <img class="neighborhood-img"
          src="https://images.unsplash.com/photo-1480074568708-e7b720bb3f09?w=600&auto=format&fit=crop&q=80"
          alt="NoDa">
        <div class="neighborhood-overlay">
          <div class="neighborhood-name">NoDa</div>
          <div class="neighborhood-count">5 Listings</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- NEWSLETTER -->
<div id="newsletter">
  <div class="newsletter-inner">
    <div class="newsletter-text">
      <p class="section-label">Market Insights</p>
      <h2 class="section-title">Stay Ahead of<br>the Market</h2>
    </div>
    <div class="newsletter-form">
      <input type="email" placeholder="Your email address">
      <button>Subscribe</button>
    </div>
  </div>
</div>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-inner">
    <div class="contact-info">
      <p class="section-label">Get In Touch</p>
      <h2 class="section-title">Let's Find Your<br><em>Next Home</em></h2>
      <p class="contact-text">Ready to buy, sell, or just explore your options? I'm here to provide expert guidance at every step of your real estate journey in the Charlotte metro area.</p>
      <div class="contact-details">
        <div class="contact-detail">
          <div class="contact-detail-icon">☎</div>
          <div>
            <div class="contact-detail-label">Phone</div>
            <a href="tel:+17045550100" class="contact-detail-value">(704) 555-0100</a>
          </div>
        </div>
        <div class="contact-detail">
          <div class="contact-detail-icon">✉</div>
          <div>
            <div class="contact-detail-label">Email</div>
            <a href="mailto:matthew@northgroupre.com" class="contact-detail-value">matthew@northgroupre.com</a>
          </div>
        </div>
        <div class="contact-detail">
          <div class="contact-detail-icon">◎</div>
          <div>
            <div class="contact-detail-label">Office</div>
            <span class="contact-detail-value">Northgroup Real Estate<br>6100 Fairview Rd, Charlotte, NC 28210</span>
          </div>
        </div>
        <div class="contact-detail">
          <div class="contact-detail-icon">★</div>
          <div>
            <div class="contact-detail-label">License</div>
            <span class="contact-detail-value">NC License #000000</span>
          </div>
        </div>
      </div>
    </div>
    <div class="contact-form">
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">First Name</label>
          <input class="form-input" type="text" placeholder="John">
        </div>
        <div class="form-group">
          <label class="form-label">Last Name</label>
          <input class="form-input" type="text" placeholder="Smith">
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Email</label>
          <input class="form-input" type="email" placeholder="john@email.com">
        </div>
        <div class="form-group">
          <label class="form-label">Phone</label>
          <input class="form-input" type="tel" placeholder="(704) 000-0000">
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">I'm Interested In</label>
        <select class="form-select form-input">
          <option value="">Select an option…</option>
          <option>Buying a Home</option>
          <option>Selling My Home</option>
          <option>Home Valuation</option>
          <option>General Inquiry</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Message</label>
        <textarea class="form-textarea" placeholder="Tell me about what you're looking for…"></textarea>
      </div>
      <div class="form-consent">
        <input type="checkbox" id="consent">
        <label for="consent">I agree to be contacted by Matthew Novak / Northgroup Real Estate via call, email, and text. Message and data rates may apply.</label>
      </div>
      <button class="form-submit">Send Message</button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <a href="#" class="logo-name">Matthew Novak</a>
      <span class="logo-sub">Northgroup Real Estate</span>
      <p class="footer-brand-text">Serving Charlotte and the surrounding communities with unparalleled market expertise, genuine care, and results-driven real estate services.</p>
      <div class="footer-social">
        <a href="#" class="social-link" title="Instagram">&#9632;</a>
        <a href="#" class="social-link" title="Facebook">f</a>
        <a href="#" class="social-link" title="LinkedIn">in</a>
        <a href="#" class="social-link" title="YouTube">▶</a>
      </div>
    </div>
    <div>
      <p class="footer-col-title">Quick Links</p>
      <ul class="footer-links">
        <li><a href="#listings">Active Listings</a></li>
        <li><a href="#listings">Open Houses</a></li>
        <li><a href="#listings">Recent Sales</a></li>
        <li><a href="#about">About Matthew</a></li>
        <li><a href="#testimonials">Client Reviews</a></li>
      </ul>
    </div>
    <div>
      <p class="footer-col-title">Services</p>
      <ul class="footer-links">
        <li><a href="#services">Buy With Me</a></li>
        <li><a href="#services">List Your Home</a></li>
        <li><a href="#contact">Home Valuation</a></li>
        <li><a href="#neighborhoods">Neighborhood Guides</a></li>
        <li><a href="#contact">Relocation</a></li>
      </ul>
    </div>
    <div>
      <p class="footer-col-title">Areas Served</p>
      <ul class="footer-links">
        <li><a href="#neighborhoods">Myers Park</a></li>
        <li><a href="#neighborhoods">Dilworth</a></li>
        <li><a href="#neighborhoods">Ballantyne</a></li>
        <li><a href="#neighborhoods">NoDa</a></li>
        <li><a href="#neighborhoods">Huntersville</a></li>
        <li><a href="#neighborhoods">Concord</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p class="footer-copy">© 2026 Matthew Novak · Northgroup Real Estate. All rights reserved. NC License #000000</p>
    <div class="footer-legal">
      <a href="#">Privacy Policy</a>
      <a href="#">Terms of Use</a>
      <a href="#">Accessibility</a>
    </div>
  </div>
</footer>

<script>
  // ── NAV SCROLL ──
  const nav = document.getElementById('main-nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  });

  // ── HERO SLIDESHOW ──
  let currentSlide = 0;
  const slides = document.querySelectorAll('.hero-slide');
  const dots = document.querySelectorAll('.hero-dot');
  function goToSlide(n) {
    slides[currentSlide].classList.remove('active');
    dots[currentSlide].classList.remove('active');
    currentSlide = n;
    slides[currentSlide].classList.add('active');
    dots[currentSlide].classList.add('active');
  }
  setInterval(() => goToSlide((currentSlide + 1) % slides.length), 5000);

  // ── SEARCH TABS ──
  function setTab(el) {
    document.querySelectorAll('.search-tab').forEach(t => t.classList.remove('active'));
    el.classList.add('active');
  }

  // ── TESTIMONIALS ──
  let currentT = 0;
  const testimonials = document.querySelectorAll('.testimonial');
  const tDotsContainer = document.getElementById('t-dots');
  testimonials.forEach((_, i) => {
    const d = document.createElement('button');
    d.className = 't-dot' + (i === 0 ? ' active' : '');
    d.onclick = () => goToTestimonial(i);
    tDotsContainer.appendChild(d);
  });
  function goToTestimonial(n) {
    testimonials[currentT].classList.remove('active');
    tDotsContainer.children[currentT].classList.remove('active');
    currentT = (n + testimonials.length) % testimonials.length;
    testimonials[currentT].classList.add('active');
    tDotsContainer.children[currentT].classList.add('active');
  }
  function prevTestimonial() { goToTestimonial(currentT - 1); }
  function nextTestimonial() { goToTestimonial(currentT + 1); }
  setInterval(() => goToTestimonial(currentT + 1), 7000);

  // ── MOBILE MENU ──
  function toggleMobileMenu() {
    document.getElementById('mobile-menu').classList.toggle('open');
  }

  // ── CONTACT FORM ──
  document.querySelector('.form-submit').addEventListener('click', function() {
    const name = document.querySelector('.form-input[placeholder="John"]').value;
    const email = document.querySelector('.form-input[type="email"]').value;
    if (!name || !email) {
      alert('Please fill in your name and email.');
      return;
    }
    this.textContent = 'Message Sent ✓';
    this.style.background = '#4a7c59';
    setTimeout(() => { this.textContent = 'Send Message'; this.style.background = ''; }, 4000);
  });

  // ── NEWSLETTER ──
  document.querySelector('.newsletter-form button').addEventListener('click', function() {
    const val = document.querySelector('.newsletter-form input').value;
    if (!val.includes('@')) { alert('Please enter a valid email.'); return; }
    this.textContent = 'Subscribed ✓';
    this.style.background = '#4a7c59';
  });

  // ── INTERSECTION OBSERVER (reveal on scroll) ──
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.listing-card, .service-card, .neighborhood-card, .stat-item').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    observer.observe(el);
  });
</script>
</body>
</html>
