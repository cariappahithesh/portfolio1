<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hithesh Cariappa · Product Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,100;0,9..144,200;0,9..144,300;1,9..144,100;1,9..144,200;1,9..144,300&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }

:root {
  --navy:    #03061f;
  --deep:    #050a2c;
  --mid:     #0a1a6e;
  --horizon: #1a5fa8;
  --sky:     #4e9bd4;
  --white:   #f5f3ef;
  --dim:     rgba(245,243,239,0.5);
  --dimmer:  rgba(245,243,239,0.28);
  --ink:     #111010;
  --muted:   #666560;
  --border:  #e6e3dc;
  --card:    #f2f0eb;
}

html { scroll-behavior: smooth; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--navy);
  color: var(--white);
  overflow-x: hidden;
  cursor: none;
}

/* ─── CURSOR ─── */
#cursor-dot {
  position: fixed; z-index: 9999; pointer-events: none;
  width: 7px; height: 7px; border-radius: 50%;
  left: 0; top: 0;
  background: #fff;
  box-shadow: 0 0 9px 3px rgba(180,220,255,0.65);
  transition: width .18s, height .18s, background .25s, box-shadow .25s;
}
#cursor-ring {
  position: fixed; z-index: 9998; pointer-events: none;
  width: 34px; height: 34px; border-radius: 50%;
  left: 0; top: 0;
  border: 1px solid rgba(180,220,255,0.38);
  transition: width .28s, height .28s, border-color .25s;
}
#cursor-trail {
  position: fixed; z-index: 9997; pointer-events: none;
  width: 88px; height: 88px; border-radius: 50%;
  left: 0; top: 0;
  background: radial-gradient(circle, rgba(100,180,255,0.10) 0%, transparent 70%);
}
/* Blue when over light background */
body.cursor-light #cursor-dot {
  background: #1a5fa8;
  box-shadow: 0 0 9px 3px rgba(26,95,168,0.32);
}
body.cursor-light #cursor-ring  { border-color: rgba(26,95,168,0.32); }
body.cursor-light #cursor-trail { background: radial-gradient(circle, rgba(26,95,168,0.07) 0%, transparent 70%); }

/* ─── CANVAS ─── */
#star-canvas {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0; pointer-events: none;
}

/* ─── NAV ─── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 26px 48px;
}
.nav-logo {
  font-family: 'Fraunces', serif;
  font-weight: 200; font-size: 15px; letter-spacing: 0.01em;
  color: rgba(255,255,255,0.88); text-decoration: none;
  border: 1px solid rgba(255,255,255,0.18);
  padding: 7px 16px; border-radius: 3px;
  background: rgba(3,6,31,0.28);
  backdrop-filter: blur(10px); -webkit-backdrop-filter: blur(10px);
  transition: border-color .3s;
}
.nav-logo:hover { border-color: rgba(255,255,255,0.48); }
.nav-links { display: flex; gap: 36px; list-style: none; }
.nav-links a {
  font-size: 13px; font-weight: 400; letter-spacing: 0.04em;
  color: rgba(255,255,255,0.62); text-decoration: none; transition: color .22s;
}
.nav-links a:hover { color: #fff; }

/* ─── HERO ─── */
#hero {
  position: relative; z-index: 1;
  min-height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  text-align: center; padding: 0 24px;
}
/* White blend at bottom of hero */
#hero::after {
  content: '';
  position: absolute; bottom: 0; left: 0; right: 0; height: 42vh;
  background: linear-gradient(to bottom,
    transparent 0%,
    rgba(245,243,239,0.04) 30%,
    rgba(245,243,239,0.50) 64%,
    rgba(245,243,239,0.94) 85%,
    #f5f3ef 100%
  );
  pointer-events: none; z-index: 2;
}
.hero-headline {
  font-family: 'Fraunces', serif;
  font-weight: 200;
  font-size: clamp(38px, 6.5vw, 82px);
  line-height: 1.12; letter-spacing: -0.025em;
  color: var(--white);
  max-width: 860px;
  opacity: 0; position: relative; z-index: 1;
  text-shadow: 0 4px 22.8px rgba(255, 255, 255, 0.40);
  animation: heroIn 1.5s cubic-bezier(.22,1,.36,1) .5s forwards;
}
.hero-headline em { font-style: italic; font-weight: 100; }
.hero-sub {
  font-size: 12px; letter-spacing: 0.16em; text-transform: uppercase;
  color: var(--dim); margin-top: 30px; font-weight: 400;
  opacity: 0; position: relative; z-index: 1;
  animation: heroIn 1.2s ease 1.05s forwards;
}
.hero-scroll {
  position: absolute; bottom: 56px; left: 50%; transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 10px;
  opacity: 0; z-index: 3;
  animation: heroIn 1s ease 2s forwards;
}
.hero-scroll span { font-size: 9px; letter-spacing: 0.18em; text-transform: uppercase; color: var(--dimmer); }
.scroll-line {
  width: 1px; height: 44px;
  background: linear-gradient(to bottom, var(--dimmer), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes heroIn {
  from { opacity:0; transform:translateY(18px); }
  to   { opacity:1; transform:translateY(0); }
}
@keyframes scrollPulse {
  0%,100% { opacity:.3; } 50% { opacity:.85; }
}

/* ─── WHITE CONTENT ─── */
.section-wrap {
  position: relative; z-index: 2;
  background: #f5f3ef; color: var(--ink);
}
.section-inner {
  max-width: 960px; margin: 0 auto; padding: 96px 48px;
}
.section-inner + .section-inner { border-top: 1px solid var(--border); }

.s-label {
  font-size: 10px; font-weight: 500; letter-spacing: 0.18em; text-transform: uppercase;
  color: #aaa; display: flex; align-items: center; gap: 12px; margin-bottom: 24px;
}
.s-label::before { content:''; width:22px; height:1px; background:#ccc; }

/* Fraunces ONLY on headings */
.s-heading {
  font-family: 'Fraunces', serif;
  font-weight: 200; font-size: clamp(34px,4.8vw,54px);
  line-height: 1.1; letter-spacing: -0.02em;
  color: var(--ink); margin-bottom: 40px;
}
.s-heading em { font-style:italic; color: var(--horizon); }

/* ─── ABOUT ─── */
.about-grid { display:grid; grid-template-columns:1fr 1fr; gap:64px; align-items:start; }
.about-body { font-size:15.5px; line-height:1.82; color:#4a4845; font-weight:300; }
.about-body p + p { margin-top:18px; }
.about-body strong { color:var(--ink); font-weight:500; }
.about-stats { display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-top:36px; }
.stat-box { background:#eeece7; border:1px solid var(--border); border-radius:10px; padding:18px 20px; }
.stat-num {
  font-family: 'Fraunces', serif;   /* display numerals = heading weight */
  font-size:34px; font-weight:200;
  color:var(--ink); letter-spacing:-0.03em;
}
.stat-num em { font-style:italic; font-size:0.58em; color:var(--horizon); }
.stat-label { font-size:11.5px; color:#999; margin-top:5px; font-weight:400; }

.skills-label { font-size:10px; font-weight:500; letter-spacing:0.14em; text-transform:uppercase; color:#aaa; margin-bottom:16px; }
.skill-group + .skill-group { margin-top:26px; }
.skill-group-name { font-size:12px; font-weight:500; color:#444; margin-bottom:9px; }
.skill-tags { display:flex; flex-wrap:wrap; gap:7px; }
.stag {
  font-size:11.5px; font-weight:400;
  background:#eae8e3; border:1px solid var(--border);
  color:#555; padding:5px 12px; border-radius:100px; transition:all .2s;
}
.stag:hover { background:var(--mid); color:#fff; border-color:var(--mid); }

/* ─── EXPERIENCE ─── */
.exp-item {
  display:grid; grid-template-columns:172px 1fr; gap:32px;
  padding:34px 0; border-bottom:1px solid var(--border);
}
.exp-item:first-child { border-top:1px solid var(--border); }
.exp-period { font-size:12px; color:#aaa; font-weight:400; line-height:1.6; }
.exp-company { font-size:14px; color:var(--horizon); margin-top:7px; font-weight:400; }
.exp-type { font-size:11px; color:#bbb; margin-top:3px; letter-spacing:0.04em; }
.exp-role {
  font-family: 'Fraunces', serif;   /* heading */
  font-size:22px; font-weight:200;
  line-height:1.2; letter-spacing:-0.01em;
  color:var(--ink); margin-bottom:14px;
}
.exp-bullets { list-style:none; }
.exp-bullets li {
  font-size:13.5px; line-height:1.75; color:#5a5855; font-weight:300;
  padding-left:18px; position:relative; margin-bottom:7px;
}
.exp-bullets li::before { content:'·'; position:absolute; left:0; color:var(--horizon); font-size:15px; top:-1px; }
.exp-bullets li strong { color:var(--ink); font-weight:500; }

/* ─── PROJECTS ─── */
.projects-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 1fr;
  gap: 18px;
  margin-top: 36px;
}
.proj-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 12px;
  padding: 26px 28px; transition: transform .28s, box-shadow .28s, border-color .28s;
  text-decoration: none; color: inherit;
  display: flex; flex-direction: column;
}
.proj-card:hover { transform: translateY(-4px); box-shadow: 0 14px 36px rgba(0,0,0,0.07); border-color: #c5d4e4; }
.proj-tag { font-size: 10px; font-weight: 500; letter-spacing: 0.13em; text-transform: uppercase; color: var(--horizon); margin-bottom: 12px; }
.proj-title {
  font-family: 'Fraunces', serif;
  font-size: 19px; font-weight: 200;
  line-height: 1.3; letter-spacing: -0.01em;
  color: var(--ink); margin-bottom: 11px;
}
.proj-desc { font-size: 13px; line-height: 1.72; color: #666; font-weight: 300; flex: 1; }
.proj-impact {
  display: inline-block; margin-top: 16px; align-self: flex-start;
  font-size: 11.5px; font-weight: 500; color: var(--horizon);
  background: rgba(26,95,168,0.08); padding: 4px 12px; border-radius: 100px;
}

/* ─── EDUCATION ─── */
.edu-block { margin-bottom:36px; }
.edu-degree {
  font-family: 'Fraunces', serif;   /* heading */
  font-size:21px; font-weight:200; letter-spacing:-0.01em; color:var(--ink); margin-bottom:4px;
}
.edu-uni { font-size:13.5px; color:#888; font-weight:300; }
.edu-period { font-size:11.5px; color:#bbb; margin-top:4px; }
.leadership-grid { display:grid; grid-template-columns:1fr 1fr 1fr; gap:18px; margin-top:28px; }
.lead-card { background:var(--card); border:1px solid var(--border); border-radius:10px; padding:20px 22px; }
.lead-role {
  font-family: 'Fraunces', serif;   /* heading */
  font-size:15px; font-weight:200; color:var(--ink); margin-bottom:5px;
}
.lead-org { font-size:11.5px; color:#999; font-weight:400; }
.lead-desc { font-size:12.5px; color:#777; margin-top:9px; line-height:1.62; font-weight:300; }

/* ─── CTA ─── */
.cta-wrap {
  text-align:center; background:var(--navy); color:var(--white);
  padding:96px 48px; position:relative; overflow:hidden; z-index:2;
}
.cta-wrap::before {
  content:''; position:absolute; inset:0;
  background:radial-gradient(ellipse at 50% 0%, rgba(26,95,168,0.45) 0%, transparent 68%);
  pointer-events:none;
}
.cta-heading {
  font-family: 'Fraunces', serif;   /* heading */
  font-size:clamp(34px,5vw,58px); font-weight:200; letter-spacing:-0.022em;
  line-height:1.1; position:relative; z-index:1;
}
.cta-heading em { font-style:italic; }
.cta-sub { font-size:14.5px; color:var(--dim); margin-top:18px; font-weight:300; position:relative; z-index:1; }
.cta-links { display:flex; gap:14px; justify-content:center; margin-top:38px; flex-wrap:wrap; position:relative; z-index:1; }
.cta-btn {
  font-size:13px; font-weight:400; color:var(--white);
  border:1px solid rgba(255,255,255,0.28); padding:11px 26px; border-radius:4px;
  text-decoration:none; letter-spacing:0.03em; transition:all .22s;
  background:rgba(255,255,255,0.05);
}
.cta-btn:hover { background:rgba(255,255,255,0.12); border-color:rgba(255,255,255,0.55); }
.cta-btn.primary { background:var(--horizon); border-color:var(--horizon); }
.cta-btn.primary:hover { background:var(--sky); border-color:var(--sky); }

/* ─── FOOTER ─── */
footer {
  background:#03061f; color:rgba(255,255,255,0.32); font-size:12px;
  padding:26px 48px; display:flex; justify-content:space-between; align-items:center;
  border-top:1px solid rgba(255,255,255,0.06); position:relative; z-index:2;
  flex-wrap:wrap; gap:10px;
}
.footer-name { font-family:'Fraunces',serif; font-weight:200; font-size:13px; color:rgba(255,255,255,0.48); }
.footer-links { display:flex; gap:22px; }
.footer-links a { color:rgba(255,255,255,0.32); text-decoration:none; font-size:12px; transition:color .2s; }
.footer-links a:hover { color:rgba(255,255,255,0.68); }

/* ─── REVEAL ─── */
.reveal { opacity:0; transform:translateY(24px); transition:opacity .75s ease,transform .75s ease; }
.reveal.visible { opacity:1; transform:none; }

/* ─── RESPONSIVE ─── */
@media (max-width:768px) {
  nav { padding:18px 20px; }
  .section-inner { padding:60px 20px; }
  .about-grid { grid-template-columns:1fr; gap:36px; }
  .exp-item { grid-template-columns:1fr; gap:10px; }
  .projects-grid { grid-template-columns:1fr; }
  .proj-card.wide { grid-template-columns:1fr; }
  .proj-card.wide .proj-left { border-right:none; border-bottom:1px solid var(--border); padding-right:0; padding-bottom:18px; }
  .leadership-grid { grid-template-columns:1fr; }
  .about-stats { grid-template-columns:1fr 1fr; }
}
</style>
</head>
<body>

<canvas id="star-canvas"></canvas>

<div id="cursor-dot"></div>
<div id="cursor-ring"></div>
<div id="cursor-trail"></div>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-logo">Hithesh Cariappa</a>
  <ul class="nav-links">
    <li><a href="#about">about</a></li>
    <li><a href="#work">work</a></li>
    <li><a href="#resume">resume</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <h1 class="hero-headline">
    creating products that balance<br>
    <em>user needs and business goals</em>
  </h1>
  <p class="hero-sub">Product · UX · Growth · Research</p>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    <span>scroll</span>
  </div>
</section>

<!-- WHITE SECTIONS -->
<div class="section-wrap">

  <!-- ABOUT -->
  <div class="section-inner" id="about">
    <div class="s-label">About</div>
    <div class="about-grid">
      <div>
        <h2 class="s-heading">Product enthusiast.<br><em>User advocate.</em></h2>
        <div class="about-body">
          <p>Hey, I'm <strong>Hithesh Cariappa</strong>, a product thinker with a background in interaction design and UX. I sit at the intersection of user empathy and business outcomes, helping teams ship products that actually solve problems.</p>
          <p>I bring together user research, data, and design thinking to build experiences that are both intuitive and measurable. Whether it's A/B testing, funnel optimisation or building AI-driven workflows. I care about the <strong>why</strong> behind every decision.</p>
          <p>Currently a <strong>Product Intern at Mygate</strong>, working on features that serve millions of residents and communities across India.</p>
        </div>
        <div class="about-stats">
          <div class="stat-box">
            <div class="stat-num">4<em>+</em></div>
            <div class="stat-label">Internships completed</div>
          </div>
          <div class="stat-box">
            <div class="stat-num">36<em>%</em></div>
            <div class="stat-label">Feed engagement lift at Mygate</div>
          </div>
          <div class="stat-box">
            <div class="stat-num">15<em>%</em></div>
            <div class="stat-label">Account setup improvement</div>
          </div>
          <div class="stat-box">
            <div class="stat-num">3<em>+</em></div>
            <div class="stat-label">Leadership roles held</div>
          </div>
        </div>
      </div>
      <div class="skills-col reveal">
        <div class="skills-label">Skills &amp; Tools</div>
        <div class="skill-group">
          <div class="skill-group-name">Product &amp; Growth</div>
          <div class="skill-tags">
            <span class="stag">User Research</span><span class="stag">A/B Testing</span>
            <span class="stag">Funnel Optimization</span><span class="stag">Product Strategy</span>
            <span class="stag">Roadmapping</span><span class="stag">GTM Strategy</span>
            <span class="stag">Prioritization</span>
          </div>
        </div>
        <div class="skill-group">
          <div class="skill-group-name">Data &amp; Automation</div>
          <div class="skill-tags">
            <span class="stag">SQL</span><span class="stag">Data Analysis</span>
            <span class="stag">Prompt Engineering</span><span class="stag">n8n</span>
            <span class="stag">Lovable</span><span class="stag">Documentation</span>
          </div>
        </div>
        <div class="skill-group">
          <div class="skill-group-name">Execution &amp; Design</div>
          <div class="skill-tags">
            <span class="stag">Wireframing</span><span class="stag">Prototyping</span>
            <span class="stag">Stakeholder Mgmt</span><span class="stag">Experimentation</span>
            <span class="stag">Adobe Creative Suite</span>
          </div>
        </div>
        <div class="skill-group">
          <div class="skill-group-name">Certifications</div>
          <div class="skill-tags">
            <span class="stag">Top Fellow, Product Space PM</span>
            <span class="stag">GrowthSchool UX Design</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- EXPERIENCE -->
  <div class="section-inner" id="work">
    <div class="s-label">Experience</div>
    <h2 class="s-heading">Where I've <em>made impact</em></h2>

    <div class="exp-item reveal">
      <div>
        <div class="exp-period">Jan 2026 to Present</div>
        <div class="exp-company">Mygate</div>
        <div class="exp-type">Product Intern</div>
      </div>
      <div>
        <div class="exp-role">Product Intern</div>
        <ul class="exp-bullets">
          <li>Conducted user research with residents and stakeholders to validate assumptions and identify pain points.</li>
          <li>Optimised content for the Local Buzz feature, improving discoverability and increasing feed engagement by <strong>36%</strong> through iterative experiments.</li>
          <li>Built automated workflows using n8n agents to streamline content research and reduce manual effort.</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal">
      <div>
        <div class="exp-period">Apr 2024 to Oct 2024</div>
        <div class="exp-company">Avasify</div>
        <div class="exp-type">Product &amp; Design Intern</div>
      </div>
      <div>
        <div class="exp-role">Product and Design Intern</div>
        <ul class="exp-bullets">
          <li>Designed a role-based onboarding flow tailored for tenants and affiliate marketers, ensuring clarity from the first interaction.</li>
          <li>Built an intuitive user access &amp; permissions system to prevent role confusion and friction.</li>
          <li>Streamlined the signup-to-dashboard journey, improving successful account setup by <strong>15%</strong>.</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal">
      <div>
        <div class="exp-period">Feb 2024 to Mar 2024</div>
        <div class="exp-company">Graviti</div>
        <div class="exp-type">Product Design Intern</div>
      </div>
      <div>
        <div class="exp-role">Product Design Intern</div>
        <ul class="exp-bullets">
          <li>Designed an onboarding flow optimised for truck drivers, improving usability, accessibility and task completion.</li>
          <li>Streamlined interactions to reduce friction for drivers with varied digital literacy.</li>
          <li>Increased onboarding completion rates by <strong>5%</strong>, leading to higher conversion and adoption.</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal">
      <div>
        <div class="exp-period">Oct 2023 to Jan 2024</div>
        <div class="exp-company">web3onwards</div>
        <div class="exp-type">UX Design Intern</div>
      </div>
      <div>
        <div class="exp-role">UX Design Intern</div>
        <ul class="exp-bullets">
          <li>Collaborated with developers, PMs and designers to deliver the landing page, movie detail page and rating workflow.</li>
          <li>Created wireframes, prototypes and interaction flows to simplify the experience for film enthusiasts.</li>
          <li>Strengthened user engagement and satisfaction metrics through deliberate UX decisions.</li>
        </ul>
      </div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section-inner" id="resume">
    <div class="s-label">Selected Work</div>
    <h2 class="s-heading">Projects that <em>moved metrics</em></h2>

    <div class="projects-grid">
      <a href="#" class="proj-card reveal">
        <div class="proj-tag">Mygate · 2026</div>
        <div class="proj-title">Local Buzz Content Optimisation</div>
        <div class="proj-desc">Led content strategy experiments on Mygate's Local Buzz feature, a community feed used by millions of residents. Through iterative A/B testing and UX improvements to discoverability, drove a 36% lift in feed engagement. Also automated the content research pipeline using n8n agents, cutting manual effort significantly.</div>
        <div class="proj-impact">+36% Feed Engagement</div>
      </a>

      <a href="#" class="proj-card reveal">
        <div class="proj-tag">Avasify · 2024</div>
        <div class="proj-title">Role-Based Onboarding &amp; Permissions</div>
        <div class="proj-desc">Designed a tailored onboarding flow for two distinct user roles: tenants and affiliate marketers, reducing confusion from the very first interaction. Built a permissions system that eliminated role friction and improved the signup-to-dashboard journey.</div>
        <div class="proj-impact">+15% Successful Account Setup</div>
      </a>

      <a href="#" class="proj-card reveal">
        <div class="proj-tag">Graviti · 2024</div>
        <div class="proj-title">Truck Driver Onboarding Flow</div>
        <div class="proj-desc">Redesigned the onboarding experience for truck drivers with varying digital literacy. Focused on accessibility, task clarity and friction reduction at every step, leading to improved completion rates and higher product adoption across the platform.</div>
        <div class="proj-impact">+5% Onboarding Completion</div>
      </a>

      <a href="#" class="proj-card reveal">
        <div class="proj-tag">web3onwards · 2023</div>
        <div class="proj-title">Film Platform UX: Rating &amp; Discovery</div>
        <div class="proj-desc">End-to-end UX for a web3 film discovery platform. Delivered wireframes, prototypes and interaction flows for the landing page, movie detail view and core rating workflow, simplifying a complex product for film enthusiasts.</div>
        <div class="proj-impact">Improved engagement &amp; satisfaction</div>
      </a>
    </div>
  </div>

  <!-- EDUCATION -->
  <div class="section-inner">
    <div class="s-label">Education &amp; Leadership</div>
    <h2 class="s-heading">Built beyond the <em>classroom</em></h2>

    <div class="edu-block reveal">
      <div class="edu-degree">Bachelor of Design in Interaction Design</div>
      <div class="edu-uni">Ramaiah University of Applied Sciences, Bengaluru</div>
      <div class="edu-period">2022 to Present · CGPA 7.1</div>
    </div>

    <div class="leadership-grid reveal">
      <div class="lead-card">
        <div class="lead-role">Vice President</div>
        <div class="lead-org">Photography Club, RUAS</div>
        <div class="lead-desc">Led a team to execute events, campaigns and collaborations across campus.</div>
      </div>
      <div class="lead-card">
        <div class="lead-role">Director of Media &amp; Communication</div>
        <div class="lead-org">Rotaract RUAS</div>
        <div class="lead-desc">Managed social media, PR strategy and communication campaigns; delivered marketing assets for events.</div>
      </div>
      <div class="lead-card">
        <div class="lead-role">Designer</div>
        <div class="lead-org">TEDx RUAS</div>
        <div class="lead-desc">Designed branding assets aligned with TEDx guidelines across digital and physical touchpoints.</div>
      </div>
    </div>
  </div>

</div><!-- /section-wrap -->

<!-- CTA -->
<div class="cta-wrap">
  <h2 class="cta-heading">Let's build something<br><em>worth launching.</em></h2>
  <p class="cta-sub">Open to product roles, research collabs and interesting problems.</p>
  <div class="cta-links">
    <a href="mailto:cariappahithesh@outlook.com" class="cta-btn primary">Get in touch</a>
    <a href="https://www.linkedin.com/in/hithesh-cariappa" class="cta-btn">LinkedIn</a>
    <a href="#" class="cta-btn">View Resume</a>
  </div>
</div>

<footer>
  <div class="footer-name">Hithesh Cariappa · Product Portfolio</div>
  <div class="footer-links">
    <a href="mailto:cariappahithesh@outlook.com">cariappahithesh@outlook.com</a>
    <a href="tel:+919483643013">+91 94836 43013</a>
    <span>Bengaluru, India</span>
  </div>
</footer>

<script>
/* ── CURSOR ── */
const dot   = document.getElementById('cursor-dot');
const ring  = document.getElementById('cursor-ring');
const trail = document.getElementById('cursor-trail');
let mx = window.innerWidth/2, my = window.innerHeight/2;
let rx = mx, ry = my, tx = mx, ty = my;

document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });

function animateCursor() {
  dot.style.left = mx+'px'; dot.style.top = my+'px';
  rx += (mx-rx)*0.14; ry += (my-ry)*0.14;
  ring.style.left = rx+'px'; ring.style.top = ry+'px';
  tx += (mx-tx)*0.07; ty += (my-ty)*0.07;
  trail.style.left = tx+'px'; trail.style.top = ty+'px';
  requestAnimationFrame(animateCursor);
}
animateCursor();

// Switch cursor colour when over the white section
const sw = document.querySelector('.section-wrap');
const cw = document.querySelector('.cta-wrap');
document.addEventListener('mousemove', () => {
  const sr = sw.getBoundingClientRect();
  const inLight = my >= sr.top && my <= sr.bottom;
  document.body.classList.toggle('cursor-light', inLight);
});

document.querySelectorAll('a,button,.proj-card,.stag,.lead-card,.stat-box').forEach(el => {
  el.addEventListener('mouseenter', () => { dot.style.width=dot.style.height='11px'; ring.style.width=ring.style.height='52px'; });
  el.addEventListener('mouseleave', () => { dot.style.width=dot.style.height='7px';  ring.style.width=ring.style.height='34px'; });
});

/* ── STAR FIELD ── */
const canvas = document.getElementById('star-canvas');
const ctx    = canvas.getContext('2d');
let W, H, stars = [];
let mox = 0.5, moy = 0.5;

function resize() { W = canvas.width = window.innerWidth; H = canvas.height = window.innerHeight; }
resize(); window.addEventListener('resize', resize);
document.addEventListener('mousemove', e => { mox = e.clientX/W; moy = e.clientY/H; });

function rand(a,b){ return a+Math.random()*(b-a); }

function initStars() {
  stars = [];
  const cols = ['#ffffff','#e8f0ff','#fff5e0','#d0e8ff','#ffe8e8','#ddf0ff'];
  for (let i = 0; i < 580; i++) {
    stars.push({
      x: Math.random(), y: Math.random(),
      r: rand(0.15,1.5),
      alpha: rand(0.10,0.75),
      speed: rand(0.003,0.021),
      phase: Math.random()*Math.PI*2,
      layer: rand(0.08,1),
      col: cols[Math.floor(Math.random()*cols.length)]
    });
  }
}
initStars();

let frame = 0;
function draw() {
  frame++;
  ctx.clearRect(0,0,W,H);

  // Background: deep navy → electric blue sky → white at horizon
  const bg = ctx.createLinearGradient(0,0,0,H);
  bg.addColorStop(0,    '#02041a');
  bg.addColorStop(0.38, '#04082e');
  bg.addColorStop(0.62, '#071238');
  bg.addColorStop(0.78, '#0d2a62');
  bg.addColorStop(0.89, '#1856a0');
  bg.addColorStop(0.95, '#4a96cc');
  bg.addColorStop(0.985,'#b8d8f0');
  bg.addColorStop(1,    '#f5f3ef');  // flush with section-wrap
  ctx.fillStyle = bg; ctx.fillRect(0,0,W,H);

  // Faint blue glow near upper centre
  const glow = ctx.createRadialGradient(W*.5,H*.22,0,W*.5,H*.22,W*.35);
  glow.addColorStop(0,'rgba(70,110,210,0.09)');
  glow.addColorStop(1,'transparent');
  ctx.fillStyle = glow; ctx.fillRect(0,0,W,H);

  // Stars — fade out before the white zone
  stars.forEach(s => {
    const twinkle = Math.sin(frame*s.speed + s.phase)*0.5+0.5;
    const sy = s.y + (moy-.5)*s.layer*0.014;
    if (sy > 0.93) return;
    const fade = sy > 0.62 ? Math.max(0, 1-(sy-.62)/(0.93-.62)) : 1;
    const a = s.alpha*(0.55+twinkle*0.45)*fade;
    const px = (s.x + (mox-.5)*s.layer*0.02)*W;
    const py = sy*H;

    ctx.globalAlpha = a;
    if (s.r > 0.8) {
      const g = ctx.createRadialGradient(px,py,0,px,py,s.r*4);
      g.addColorStop(0, s.col);
      g.addColorStop(0.35,'rgba(200,220,255,0.18)');
      g.addColorStop(1,'transparent');
      ctx.fillStyle = g;
      ctx.beginPath(); ctx.arc(px,py,s.r*4,0,Math.PI*2); ctx.fill();
    }
    ctx.fillStyle = s.col;
    ctx.beginPath(); ctx.arc(px,py,s.r*(0.8+twinkle*0.28),0,Math.PI*2); ctx.fill();
  });

  ctx.globalAlpha = 1;
  requestAnimationFrame(draw);
}
draw();

/* ── SCROLL REVEAL ── */
const revEls = document.querySelectorAll('.reveal');
new IntersectionObserver((entries, io) => {
  entries.forEach((e,i) => {
    if (e.isIntersecting) {
      setTimeout(() => e.target.classList.add('visible'), i*55);
      io.unobserve(e.target);
    }
  });
},{ threshold:0.1 }).observe && (() => {
  const io = new IntersectionObserver((entries) => {
    entries.forEach((e,i) => {
      if (e.isIntersecting) { setTimeout(()=>e.target.classList.add('visible'),i*55); }
    });
  },{threshold:0.1});
  revEls.forEach(el => io.observe(el));
})();

/* ── SMOOTH SCROLL ── */
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const t = document.querySelector(a.getAttribute('href'));
    if (t) { e.preventDefault(); t.scrollIntoView({behavior:'smooth'}); }
  });
});
</script>
</body>
</html>
