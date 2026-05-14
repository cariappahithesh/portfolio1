<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Your Name | Product & Design</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=DM+Sans:wght@300;400;500;600&family=Syne:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #F5F2EC;
    --bg-dark: #111110;
    --text: #111110;
    --text-muted: #7a7a72;
    --accent: #D4551F;
    --accent-warm: #E8855A;
    --card-bg: #EDEAE3;
    --border: #dedad2;
    --white: #FDFCF9;
    --radius: 16px;
    --radius-sm: 10px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s ease, width 0.2s ease, height 0.2s ease, background 0.2s ease;
    mix-blend-mode: multiply;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--accent);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.15s ease, width 0.2s ease, height 0.2s ease, opacity 0.2s ease;
    opacity: 0.5;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 50%; transform: translateX(-50%);
    z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    width: min(760px, calc(100% - 40px));
    padding: 10px 16px;
    background: rgba(245, 242, 236, 0.88);
    backdrop-filter: blur(14px);
    border: 1px solid var(--border);
    border-radius: 100px;
    margin-top: 16px;
    gap: 12px;
  }
  .nav-brand {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 15px;
    letter-spacing: -0.02em;
    color: var(--text);
    text-decoration: none;
    display: flex; align-items: center; gap: 8px;
  }
  .nav-dot {
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.8); }
  }
  .nav-links {
    display: flex; align-items: center; gap: 4px;
    list-style: none;
  }
  .nav-links a {
    font-size: 13px;
    font-weight: 500;
    color: var(--text-muted);
    text-decoration: none;
    padding: 6px 12px;
    border-radius: 100px;
    transition: all 0.2s ease;
  }
  .nav-links a:hover { color: var(--text); background: var(--card-bg); }
  .nav-cta {
    background: var(--text) !important;
    color: var(--bg) !important;
    padding: 7px 16px !important;
  }
  .nav-cta:hover { background: var(--accent) !important; }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center;
    padding: 100px 24px 60px;
    max-width: 1100px;
    margin: 0 auto;
    position: relative;
  }
  .hero-tag {
    display: inline-flex; align-items: center; gap: 8px;
    font-size: 12px;
    font-weight: 500;
    color: var(--text-muted);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.1s forwards;
  }
  .hero-tag span {
    width: 24px; height: 1px; background: var(--text-muted);
  }
  .hero-headline {
    font-family: 'Instrument Serif', serif;
    font-size: clamp(52px, 8vw, 100px);
    line-height: 1.0;
    letter-spacing: -0.03em;
    color: var(--text);
    max-width: 900px;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.2s forwards;
  }
  .hero-headline em {
    font-style: italic;
    color: var(--accent);
  }
  .hero-sub {
    font-size: clamp(16px, 2vw, 20px);
    line-height: 1.6;
    color: var(--text-muted);
    max-width: 540px;
    margin-top: 28px;
    font-weight: 400;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.35s forwards;
  }
  .hero-actions {
    display: flex; align-items: center; gap: 16px;
    margin-top: 40px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.5s forwards;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--text);
    color: var(--bg);
    font-size: 14px; font-weight: 500;
    padding: 12px 24px;
    border-radius: 100px;
    text-decoration: none;
    transition: all 0.25s ease;
    border: none; cursor: none;
  }
  .btn-primary:hover { background: var(--accent); transform: translateY(-2px); }
  .btn-secondary {
    display: inline-flex; align-items: center; gap: 8px;
    background: transparent;
    color: var(--text);
    font-size: 14px; font-weight: 500;
    padding: 12px 24px;
    border-radius: 100px;
    text-decoration: none;
    border: 1.5px solid var(--border);
    transition: all 0.25s ease;
    cursor: none;
  }
  .btn-secondary:hover { border-color: var(--text); transform: translateY(-2px); }
  .social-pill {
    display: inline-flex; align-items: center; gap: 6px;
    font-size: 12px; font-weight: 500;
    color: var(--text-muted);
    background: var(--card-bg);
    padding: 6px 12px;
    border-radius: 100px;
    text-decoration: none;
    transition: all 0.2s ease;
    border: 1px solid var(--border);
  }
  .social-pill:hover { color: var(--text); transform: translateY(-2px); }
  .hero-socials {
    display: flex; gap: 8px; align-items: center; margin-top: 12px;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.65s forwards;
  }
  .hero-scroll {
    position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    opacity: 0;
    animation: fadeIn 1s ease 1s forwards;
  }
  .hero-scroll span {
    font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase;
    color: var(--text-muted); font-weight: 500;
  }
  .scroll-line {
    width: 1px; height: 40px; background: var(--border);
    animation: scrollDown 1.5s ease-in-out infinite;
  }
  @keyframes scrollDown {
    0% { transform: scaleY(0); transform-origin: top; }
    50% { transform: scaleY(1); transform-origin: top; }
    51% { transform: scaleY(1); transform-origin: bottom; }
    100% { transform: scaleY(0); transform-origin: bottom; }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  /* SECTION COMMONS */
  section { padding: 100px 24px; max-width: 1100px; margin: 0 auto; }
  .section-label {
    font-size: 11px; font-weight: 600;
    letter-spacing: 0.12em; text-transform: uppercase;
    color: var(--text-muted);
    display: flex; align-items: center; gap: 10px;
    margin-bottom: 48px;
  }
  .section-label::before {
    content: ''; width: 20px; height: 1px; background: var(--text-muted);
  }
  .section-heading {
    font-family: 'Instrument Serif', serif;
    font-size: clamp(36px, 5vw, 56px);
    line-height: 1.1;
    letter-spacing: -0.02em;
  }

  /* DIVIDER */
  .divider {
    width: 100%; height: 1px;
    background: var(--border);
    max-width: 1100px;
    margin: 0 auto;
  }

  /* PROJECTS */
  #projects { padding-top: 80px; }
  .projects-header {
    display: flex; align-items: flex-end; justify-content: space-between;
    margin-bottom: 48px; flex-wrap: wrap; gap: 20px;
  }
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  .project-card {
    background: var(--card-bg);
    border-radius: var(--radius);
    overflow: hidden;
    text-decoration: none;
    color: var(--text);
    border: 1px solid var(--border);
    transition: all 0.35s ease;
    display: flex; flex-direction: column;
    position: relative;
  }
  .project-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 24px 60px rgba(0,0,0,0.1);
    border-color: transparent;
  }
  .project-card:hover .project-arrow { opacity: 1; transform: translate(0, 0); }
  .project-img {
    width: 100%; aspect-ratio: 16/10;
    object-fit: cover;
    background: var(--border);
    position: relative;
    overflow: hidden;
  }
  .project-img-placeholder {
    width: 100%; aspect-ratio: 16/10;
    display: flex; align-items: center; justify-content: center;
    font-size: 48px;
    background: linear-gradient(135deg, var(--border) 0%, var(--card-bg) 100%);
  }
  .project-info {
    padding: 24px;
    flex: 1;
    display: flex; flex-direction: column; gap: 10px;
  }
  .project-tag {
    font-size: 11px; font-weight: 600;
    letter-spacing: 0.08em; text-transform: uppercase;
    color: var(--accent);
  }
  .project-title {
    font-family: 'Syne', sans-serif;
    font-size: 18px; font-weight: 700;
    line-height: 1.3;
    letter-spacing: -0.01em;
  }
  .project-desc {
    font-size: 13px; color: var(--text-muted);
    line-height: 1.6;
  }
  .project-footer {
    display: flex; align-items: center; justify-content: space-between;
    margin-top: auto; padding-top: 16px;
    border-top: 1px solid var(--border);
  }
  .project-chips {
    display: flex; gap: 6px; flex-wrap: wrap;
  }
  .chip {
    font-size: 11px; font-weight: 500;
    background: var(--bg);
    color: var(--text-muted);
    padding: 4px 10px;
    border-radius: 100px;
    border: 1px solid var(--border);
  }
  .project-arrow {
    width: 32px; height: 32px;
    background: var(--text);
    color: var(--bg);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    opacity: 0;
    transform: translate(-8px, 8px);
    transition: all 0.3s ease;
    flex-shrink: 0;
  }
  .project-card.featured {
    grid-column: 1 / -1;
    flex-direction: row;
  }
  .project-card.featured .project-img-placeholder {
    width: 45%;
    aspect-ratio: auto;
    min-height: 260px;
  }
  .project-card.featured .project-info {
    padding: 36px;
  }
  .project-card.featured .project-title { font-size: 22px; }

  /* ABOUT */
  #about {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }
  .about-text p {
    font-size: 16px; line-height: 1.75;
    color: var(--text-muted);
    margin-bottom: 20px;
  }
  .about-text p strong { color: var(--text); font-weight: 600; }
  .about-text p a { color: var(--accent); text-decoration: none; }
  .about-text p a:hover { text-decoration: underline; }
  .skills-section { margin-top: 40px; }
  .skills-label {
    font-size: 11px; font-weight: 600; letter-spacing: 0.1em;
    text-transform: uppercase; color: var(--text-muted);
    margin-bottom: 16px;
  }
  .skills-wrap {
    display: flex; flex-wrap: wrap; gap: 8px;
  }
  .skill-tag {
    font-size: 13px; font-weight: 500;
    background: var(--card-bg);
    color: var(--text);
    padding: 8px 16px;
    border-radius: 100px;
    border: 1px solid var(--border);
    transition: all 0.2s ease;
  }
  .skill-tag:hover { background: var(--text); color: var(--bg); }
  .about-visual { position: relative; }
  .about-photo-stack {
    position: relative;
    width: 100%;
    height: 480px;
  }
  .about-photo-card {
    position: absolute;
    border-radius: var(--radius);
    overflow: hidden;
    border: 4px solid var(--white);
    box-shadow: 0 16px 48px rgba(0,0,0,0.12);
  }
  .photo-placeholder {
    display: flex; align-items: center; justify-content: center;
    font-size: 56px;
    background: linear-gradient(135deg, var(--border), var(--card-bg));
  }
  .about-photo-card:nth-child(1) {
    width: 72%; height: 70%;
    top: 0; right: 0;
    transform: rotate(2deg);
  }
  .about-photo-card:nth-child(2) {
    width: 55%; height: 50%;
    bottom: 20px; left: 0;
    transform: rotate(-3deg);
    z-index: 2;
  }
  .about-photo-card .photo-placeholder { width: 100%; height: 100%; }

  /* EXPERIENCE */
  #experience { padding: 80px 24px; }
  .exp-list { margin-top: 48px; }
  .exp-item {
    display: flex; gap: 24px;
    padding: 28px 0;
    border-bottom: 1px solid var(--border);
    align-items: flex-start;
    transition: all 0.25s ease;
  }
  .exp-item:first-child { border-top: 1px solid var(--border); }
  .exp-item:hover .exp-content { transform: translateX(6px); }
  .exp-logo {
    width: 52px; height: 52px;
    border-radius: var(--radius-sm);
    background: var(--card-bg);
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
  }
  .exp-content { transition: transform 0.3s ease; }
  .exp-role {
    font-family: 'Syne', sans-serif;
    font-size: 17px; font-weight: 700;
    letter-spacing: -0.01em;
  }
  .exp-company {
    font-size: 14px; color: var(--text-muted);
    margin-top: 4px;
  }
  .exp-period {
    font-size: 12px; font-weight: 500;
    color: var(--accent);
    letter-spacing: 0.04em;
    margin-top: 8px;
    background: rgba(212, 85, 31, 0.1);
    display: inline-block;
    padding: 3px 10px;
    border-radius: 100px;
  }

  /* TOOLKIT */
  #toolkit { padding: 80px 24px; }
  .toolkit-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 16px;
    margin-top: 48px;
  }
  .tool-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px 16px;
    text-align: center;
    transition: all 0.25s ease;
  }
  .tool-card:hover {
    transform: translateY(-4px);
    background: var(--white);
    box-shadow: 0 12px 32px rgba(0,0,0,0.08);
  }
  .tool-icon { font-size: 28px; margin-bottom: 10px; }
  .tool-name {
    font-family: 'Syne', sans-serif;
    font-size: 14px; font-weight: 700;
    letter-spacing: -0.01em;
  }
  .tool-cat {
    font-size: 11px; color: var(--text-muted);
    margin-top: 4px;
  }

  /* TESTIMONIALS */
  #testimonials { padding: 80px 24px; overflow: hidden; }
  .testimonials-track {
    display: flex; gap: 20px;
    margin-top: 48px;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scrollbar-width: none;
    -ms-overflow-style: none;
    padding-bottom: 8px;
  }
  .testimonials-track::-webkit-scrollbar { display: none; }
  .testimonial-card {
    min-width: 360px;
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 32px;
    scroll-snap-align: start;
    transition: all 0.25s ease;
    flex-shrink: 0;
  }
  .testimonial-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 16px 48px rgba(0,0,0,0.08);
  }
  .t-quote {
    font-family: 'Instrument Serif', serif;
    font-size: 18px;
    line-height: 1.6;
    color: var(--text);
    margin-bottom: 28px;
    position: relative;
  }
  .t-quote::before {
    content: '"';
    font-size: 64px;
    color: var(--accent);
    opacity: 0.2;
    position: absolute;
    top: -20px; left: -8px;
    font-family: 'Instrument Serif', serif;
    line-height: 1;
  }
  .t-author { display: flex; align-items: center; gap: 14px; }
  .t-avatar {
    width: 44px; height: 44px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent-warm), var(--accent));
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
    color: white;
    font-weight: 600;
    flex-shrink: 0;
  }
  .t-name {
    font-family: 'Syne', sans-serif;
    font-size: 15px; font-weight: 700;
  }
  .t-title { font-size: 12px; color: var(--text-muted); margin-top: 2px; }
  .testimonial-controls {
    display: flex; gap: 12px; margin-top: 28px;
  }
  .t-btn {
    width: 44px; height: 44px;
    border-radius: 50%;
    background: var(--card-bg);
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    cursor: none;
    transition: all 0.2s ease;
  }
  .t-btn:hover { background: var(--text); color: var(--bg); }
  .t-btn svg { width: 18px; height: 18px; }

  /* CTA */
  #cta {
    padding: 80px 24px 120px;
    text-align: center;
    display: block;
    max-width: 800px;
  }
  .cta-box {
    background: var(--text);
    border-radius: 24px;
    padding: 72px 48px;
    position: relative;
    overflow: hidden;
  }
  .cta-box::before {
    content: '';
    position: absolute;
    width: 400px; height: 400px;
    background: radial-gradient(circle, var(--accent) 0%, transparent 70%);
    top: -200px; right: -100px;
    opacity: 0.3;
    pointer-events: none;
  }
  .cta-box::after {
    content: '';
    position: absolute;
    width: 300px; height: 300px;
    background: radial-gradient(circle, var(--accent-warm) 0%, transparent 70%);
    bottom: -150px; left: -50px;
    opacity: 0.15;
    pointer-events: none;
  }
  .cta-box h2 {
    font-family: 'Instrument Serif', serif;
    font-size: clamp(32px, 5vw, 52px);
    line-height: 1.15;
    letter-spacing: -0.02em;
    color: var(--white);
    margin-bottom: 20px;
    position: relative; z-index: 1;
  }
  .cta-box h2 em { font-style: italic; color: var(--accent-warm); }
  .cta-box p {
    font-size: 16px;
    color: rgba(255,255,255,0.6);
    margin-bottom: 40px;
    position: relative; z-index: 1;
  }
  .cta-btns {
    display: flex; gap: 12px; justify-content: center; flex-wrap: wrap;
    position: relative; z-index: 1;
  }
  .btn-cta-primary {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--accent);
    color: white;
    font-size: 15px; font-weight: 500;
    padding: 14px 28px;
    border-radius: 100px;
    text-decoration: none;
    transition: all 0.25s ease;
  }
  .btn-cta-primary:hover { background: var(--accent-warm); transform: translateY(-2px); }
  .btn-cta-secondary {
    display: inline-flex; align-items: center; gap: 8px;
    background: transparent;
    color: var(--white);
    font-size: 15px; font-weight: 500;
    padding: 14px 28px;
    border-radius: 100px;
    text-decoration: none;
    border: 1.5px solid rgba(255,255,255,0.25);
    transition: all 0.25s ease;
  }
  .btn-cta-secondary:hover { border-color: rgba(255,255,255,0.6); transform: translateY(-2px); }

  /* FOOTER */
  footer {
    background: var(--bg-dark);
    color: var(--white);
    padding: 56px 24px;
  }
  .footer-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: flex; justify-content: space-between; align-items: flex-end;
    flex-wrap: wrap; gap: 32px;
  }
  .footer-brand {
    font-family: 'Syne', sans-serif;
    font-size: 28px; font-weight: 800;
    letter-spacing: -0.03em;
  }
  .footer-sub { font-size: 13px; color: rgba(255,255,255,0.4); margin-top: 6px; }
  .footer-links {
    display: flex; gap: 8px; align-items: center;
  }
  .footer-link {
    width: 40px; height: 40px;
    border-radius: 50%;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.12);
    display: flex; align-items: center; justify-content: center;
    color: rgba(255,255,255,0.6);
    text-decoration: none;
    font-size: 14px;
    transition: all 0.2s ease;
  }
  .footer-link:hover { background: var(--accent); color: white; border-color: var(--accent); }
  .footer-copy {
    max-width: 1100px;
    margin: 32px auto 0;
    font-size: 12px;
    color: rgba(255,255,255,0.25);
    padding-top: 24px;
    border-top: 1px solid rgba(255,255,255,0.08);
  }

  /* MARQUEE */
  .marquee-section {
    padding: 40px 0;
    overflow: hidden;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    background: var(--card-bg);
  }
  .marquee-track {
    display: flex; gap: 48px;
    animation: marquee 20s linear infinite;
    white-space: nowrap;
  }
  .marquee-section:hover .marquee-track { animation-play-state: paused; }
  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }
  .marquee-item {
    font-family: 'Instrument Serif', serif;
    font-size: 20px;
    color: var(--text-muted);
    display: flex; align-items: center; gap: 20px;
    flex-shrink: 0;
  }
  .marquee-item span { color: var(--accent); font-style: italic; }
  .marquee-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    opacity: 0.5;
  }

  /* SCROLL ANIMATIONS */
  .reveal {
    opacity: 0;
    transform: translateY(32px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    nav { width: calc(100% - 32px); }
    .nav-links li:not(:last-child):not(:nth-last-child(2)) { display: none; }
    .projects-grid { grid-template-columns: 1fr; }
    .project-card.featured { flex-direction: column; }
    .project-card.featured .project-img-placeholder { width: 100%; min-height: 180px; }
    #about { grid-template-columns: 1fr; gap: 48px; }
    .about-photo-stack { height: 320px; }
    .cta-box { padding: 48px 24px; }
    section { padding: 60px 20px; }
  }
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-brand">
    <div class="nav-dot"></div>
    YourName
  </a>
  <ul class="nav-links">
    <li><a href="#projects">Work</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#cta" class="nav-cta">Let's Connect</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-tag"><span></span>Available for opportunities</div>
  <h1 class="hero-headline">
    Hello, I'm<br>
    <em>Your Name</em><br>
    Designer, Builder &<br>Problem Solver.
  </h1>
  <p class="hero-sub">
    A multi-disciplinary product generalist crafting impactful design experiences that stand out — blending strategy, aesthetics & craft.
  </p>
  <div class="hero-actions">
    <a href="#projects" class="btn-primary">
      View Work
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </a>
    <a href="#" class="btn-secondary">
      Download Resume
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4M7 10l5 5 5-5M12 15V3"/></svg>
    </a>
  </div>
  <div class="hero-socials">
    <a href="#" class="social-pill">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.741l7.73-8.835L1.254 2.25H8.08l4.258 5.63 5.906-5.63zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
      Twitter / X
    </a>
    <a href="#" class="social-pill">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z M4 6a2 2 0 100-4 2 2 0 000 4z"/></svg>
      LinkedIn
    </a>
    <a href="#" class="social-pill">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
      Instagram
    </a>
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-section">
  <div class="marquee-track" id="marquee">
    <div class="marquee-item">Product Design <span class="marquee-dot"></span></div>
    <div class="marquee-item">UI/UX Design <span class="marquee-dot"></span></div>
    <div class="marquee-item">Growth Strategy <span class="marquee-dot"></span></div>
    <div class="marquee-item">Vibe Coding <span class="marquee-dot"></span></div>
    <div class="marquee-item">Design Systems <span class="marquee-dot"></span></div>
    <div class="marquee-item">Micro-Interactions <span class="marquee-dot"></span></div>
    <div class="marquee-item">UX Research <span class="marquee-dot"></span></div>
    <div class="marquee-item">Prototyping <span class="marquee-dot"></span></div>
    <div class="marquee-item">Product Design <span class="marquee-dot"></span></div>
    <div class="marquee-item">UI/UX Design <span class="marquee-dot"></span></div>
    <div class="marquee-item">Growth Strategy <span class="marquee-dot"></span></div>
    <div class="marquee-item">Vibe Coding <span class="marquee-dot"></span></div>
    <div class="marquee-item">Design Systems <span class="marquee-dot"></span></div>
    <div class="marquee-item">Micro-Interactions <span class="marquee-dot"></span></div>
    <div class="marquee-item">UX Research <span class="marquee-dot"></span></div>
    <div class="marquee-item">Prototyping <span class="marquee-dot"></span></div>
  </div>
</div>

<!-- PROJECTS -->
<section id="projects" style="max-width:1100px;margin:0 auto;padding:80px 24px;">
  <div class="projects-header">
    <div>
      <div class="section-label">Selected Work</div>
      <h2 class="section-heading">Featured Projects</h2>
    </div>
    <a href="#" class="btn-secondary" style="height:fit-content;">
      View All Work
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </a>
  </div>

  <div class="projects-grid reveal">
    <!-- Featured Card -->
    <a href="#" class="project-card featured">
      <div class="project-img-placeholder">🛒</div>
      <div class="project-info">
        <span class="project-tag">UX / App Design • 2025</span>
        <h3 class="project-title">Revamping the App MVP to Enhance Usability</h3>
        <p class="project-desc">End-to-end redesign of a B2B grocery platform, focusing on reducing friction and improving user retention with a cleaner IA and updated components.</p>
        <div class="project-footer">
          <div class="project-chips">
            <span class="chip">Research</span>
            <span class="chip">UI Design</span>
            <span class="chip">Figma</span>
          </div>
          <div class="project-arrow">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
        </div>
      </div>
    </a>

    <!-- Card 2 -->
    <a href="#" class="project-card reveal">
      <div class="project-img-placeholder" style="font-size:36px;">🌿</div>
      <div class="project-info">
        <span class="project-tag">Web Design • Personal Project</span>
        <h3 class="project-title">Designing a Website Focused on Trust</h3>
        <p class="project-desc">Crafted a trust-forward brand site with deliberate use of social proof, micro-copy and editorial layouts to boost conversion.</p>
        <div class="project-footer">
          <div class="project-chips">
            <span class="chip">Web Design</span>
            <span class="chip">Framer</span>
          </div>
          <div class="project-arrow">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
        </div>
      </div>
    </a>

    <!-- Card 3 -->
    <a href="#" class="project-card reveal">
      <div class="project-img-placeholder" style="font-size:36px;">🤖</div>
      <div class="project-info">
        <span class="project-tag">Product Design • Personal Project</span>
        <h3 class="project-title">AI Grocery App Focused on Savings</h3>
        <p class="project-desc">Designed an AI-powered grocery assistant that helps users save money by surfacing deals and predicting weekly shopping lists.</p>
        <div class="project-footer">
          <div class="project-chips">
            <span class="chip">AI Product</span>
            <span class="chip">iOS Design</span>
          </div>
          <div class="project-arrow">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
        </div>
      </div>
    </a>

    <!-- Card 4 -->
    <a href="#" class="project-card reveal">
      <div class="project-img-placeholder" style="font-size:36px;">📈</div>
      <div class="project-info">
        <span class="project-tag">Web Design • 2025</span>
        <h3 class="project-title">Reimagining the Website — Focusing on Conversion</h3>
        <p class="project-desc">Full website revamp with a conversion-first approach — rebuilt the hero, restructured the pricing page and added interactive elements.</p>
        <div class="project-footer">
          <div class="project-chips">
            <span class="chip">Growth</span>
            <span class="chip">Conversion</span>
            <span class="chip">Framer</span>
          </div>
          <div class="project-arrow">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
        </div>
      </div>
    </a>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="about-text reveal">
    <div class="section-label">About Me</div>
    <h2 class="section-heading" style="margin-bottom:32px;">
      Product Generalist.<br>Designer. Storyteller<br>& <em style="font-style:italic;color:var(--accent)">more.</em>
    </h2>
    <p>Hey! I'm <strong>Your Name</strong>. A multi-faceted individual who's been dabbling with curious pursuits since I've been young. After my initial career experience in usability testing, I eventually discovered the crosspath between design & functional experiences.</p>
    <p>With a sharp eye for detail and a drive to craft meaningful experiences, I work on building powerful products that let enterprises and developers <a href="#">move faster and smarter</a>.</p>
    <p>Apart from work — cinema, cameras, my love for fitness & travel are my escapades. As a product catalyst, I thrive on delivering scalable solutions that balance functionality and aesthetics.</p>
    <div class="skills-section">
      <div class="skills-label">Few of my top skills</div>
      <div class="skills-wrap">
        <span class="skill-tag">Web Design</span>
        <span class="skill-tag">UI Design</span>
        <span class="skill-tag">Vibe Coding</span>
        <span class="skill-tag">Micro-Interactions</span>
        <span class="skill-tag">Copywriting</span>
        <span class="skill-tag">UX Research</span>
        <span class="skill-tag">Prototyping</span>
        <span class="skill-tag">Design Thinking</span>
      </div>
    </div>
    <div style="margin-top:36px;">
      <a href="#" class="btn-primary">Know More About Me</a>
    </div>
  </div>

  <div class="about-visual reveal">
    <div class="about-photo-stack">
      <div class="about-photo-card">
        <div class="photo-placeholder">🏖️</div>
      </div>
      <div class="about-photo-card">
        <div class="photo-placeholder">📸</div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- EXPERIENCE -->
<section id="experience" style="max-width:1100px;margin:0 auto;padding:80px 24px;">
  <div class="section-label">Career Journey</div>
  <h2 class="section-heading">Experience</h2>
  <div class="exp-list">
    <div class="exp-item reveal">
      <div class="exp-logo">🚀</div>
      <div class="exp-content">
        <div class="exp-role">Founding Member (Growth & Design)</div>
        <div class="exp-company">Flexprice — Billing & Pricing Infrastructure</div>
        <div class="exp-period">June 2025 – Current</div>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-logo">🛒</div>
      <div class="exp-content">
        <div class="exp-role">Product Design Consultant</div>
        <div class="exp-company">KiranaPro — B2B Grocery Platform</div>
        <div class="exp-period">Feb 2025 – June 2025</div>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-logo">🎨</div>
      <div class="exp-content">
        <div class="exp-role">Cohort Member</div>
        <div class="exp-company">10kDesigners Bootcamp</div>
        <div class="exp-period">Jan 2025 – May 2025</div>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-logo">💼</div>
      <div class="exp-content">
        <div class="exp-role">ASE – Quality Associate</div>
        <div class="exp-company">Accenture</div>
        <div class="exp-period">July 2023 – May 2025</div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- TOOLKIT -->
<section id="toolkit" style="max-width:1100px;margin:0 auto;padding:80px 24px;">
  <div class="section-label">Tools I Use</div>
  <h2 class="section-heading">What's in my toolkit?</h2>
  <div class="toolkit-grid reveal">
    <div class="tool-card">
      <div class="tool-icon">🎨</div>
      <div class="tool-name">Figma</div>
      <div class="tool-cat">Product Design</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">⚡</div>
      <div class="tool-name">Cursor</div>
      <div class="tool-cat">Design Engineering</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">🤖</div>
      <div class="tool-name">Claude</div>
      <div class="tool-cat">Task Automation</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">🖼️</div>
      <div class="tool-name">Framer</div>
      <div class="tool-cat">Live Site Design</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">💡</div>
      <div class="tool-name">Mobbin</div>
      <div class="tool-cat">Inspiration</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">🎬</div>
      <div class="tool-name">Loom</div>
      <div class="tool-cat">Feedback Loops</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">✨</div>
      <div class="tool-name">LottieFiles</div>
      <div class="tool-cat">Quick Animations</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">🌐</div>
      <div class="tool-name">Arc</div>
      <div class="tool-cat">Super-Browser</div>
    </div>
    <div class="tool-card">
      <div class="tool-icon">🖼</div>
      <div class="tool-name">Midjourney</div>
      <div class="tool-cat">Images & Art</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- TESTIMONIALS -->
<section id="testimonials" style="max-width:1100px;margin:0 auto;padding:80px 24px;">
  <div class="section-label">What People Say</div>
  <h2 class="section-heading" style="margin-bottom:0">Kind Words</h2>
  <div class="testimonials-track" id="testimonialsTrack">
    <div class="testimonial-card reveal">
      <p class="t-quote">Working with them was a smooth ride. They put their 100% at anything they do. High agency, adapts to need & has an appetite to learn.</p>
      <div class="t-author">
        <div class="t-avatar">A</div>
        <div>
          <div class="t-name">Arjun Unni</div>
          <div class="t-title">Sr. Product Designer at Tesco</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card reveal">
      <p class="t-quote">A talented designer who consistently brings fresh ideas to the table. Their ability to craft delightful user experiences made it a pleasure to work alongside them.</p>
      <div class="t-author">
        <div class="t-avatar" style="background: linear-gradient(135deg,#6C63FF,#4a46c4);">B</div>
        <div>
          <div class="t-name">Bhavarth Bhati</div>
          <div class="t-title">Product Designer at KiranaPro</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card reveal">
      <p class="t-quote">With minimal input, they quickly understood the idea & delivered designs that added instant value. Truly impressive product instincts.</p>
      <div class="t-author">
        <div class="t-avatar" style="background: linear-gradient(135deg,#11998e,#38ef7d);">A</div>
        <div>
          <div class="t-name">Alok Mishra</div>
          <div class="t-title">Country Head, QodeNext</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card reveal">
      <p class="t-quote">An impactful player when it comes to design. I've witnessed stellar work and I'm sure they will do wonders in whatever they pursue next.</p>
      <div class="t-author">
        <div class="t-avatar" style="background: linear-gradient(135deg,#f7971e,#ffd200);">D</div>
        <div>
          <div class="t-name">Deepak Ravindran</div>
          <div class="t-title">CEO, KiranaPro</div>
        </div>
      </div>
    </div>
  </div>
  <div class="testimonial-controls">
    <button class="t-btn" id="tPrev" aria-label="Previous">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M15 19l-7-7 7-7"/></svg>
    </button>
    <button class="t-btn" id="tNext" aria-label="Next">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 5l7 7-7 7"/></svg>
    </button>
  </div>
</section>

<div class="divider"></div>

<!-- CTA -->
<section id="cta" style="max-width:900px;margin:0 auto;padding:80px 24px 120px;">
  <div class="cta-box reveal">
    <h2>Curious about my work?<br>Let's <em>chat.</em></h2>
    <p>Open to design roles, consulting & building things that actually matter.</p>
    <div class="cta-btns">
      <a href="mailto:hello@yourname.com" class="btn-cta-primary">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Reach Out
      </a>
      <a href="#" class="btn-cta-secondary">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
        Book a Call
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div>
      <div class="footer-brand">YourName.</div>
      <div class="footer-sub">Designer · Builder · Product Generalist</div>
    </div>
    <div class="footer-links">
      <a href="#" class="footer-link" title="Twitter">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.741l7.73-8.835L1.254 2.25H8.08l4.258 5.63 5.906-5.63zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
      </a>
      <a href="#" class="footer-link" title="LinkedIn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z M4 6a2 2 0 100-4 2 2 0 000 4z"/></svg>
      </a>
      <a href="#" class="footer-link" title="Instagram">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
      </a>
      <a href="#hero" class="footer-link" title="Back to top" style="margin-left:8px; background:rgba(255,255,255,0.05);">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 19V5M5 12l7-7 7 7"/></svg>
      </a>
    </div>
  </div>
  <div class="footer-copy">
    © 2025 YourName. Designed & built with care. All rights reserved.
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.transform = `translate(${mx - 6}px, ${my - 6}px)`;
  });
  function animateRing() {
    rx += (mx - rx - 18) * 0.12;
    ry += (my - ry - 18) * 0.12;
    ring.style.transform = `translate(${rx}px, ${ry}px)`;
    requestAnimationFrame(animateRing);
  }
  animateRing();
  document.querySelectorAll('a, button, .project-card, .tool-card, .testimonial-card, .skill-tag').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '20px'; cursor.style.height = '20px';
      ring.style.width = '50px'; ring.style.height = '50px';
      ring.style.opacity = '0.3';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '12px'; cursor.style.height = '12px';
      ring.style.width = '36px'; ring.style.height = '36px';
      ring.style.opacity = '0.5';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        e.target.style.transitionDelay = `${i * 0.05}s`;
        e.target.classList.add('visible');
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => io.observe(el));

  // Testimonials scroll
  const track = document.getElementById('testimonialsTrack');
  document.getElementById('tNext').addEventListener('click', () => {
    track.scrollBy({ left: 380, behavior: 'smooth' });
  });
  document.getElementById('tPrev').addEventListener('click', () => {
    track.scrollBy({ left: -380, behavior: 'smooth' });
  });

  // Duplicate marquee content
  const marquee = document.getElementById('marquee');
  marquee.innerHTML += marquee.innerHTML;
</script>
</body>
</html>
