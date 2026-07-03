<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Martin Karani | IT Portfolio 2026</title>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;600;700&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
/* ── RESET ── */
*{margin:0;padding:0;box-sizing:border-box;}

/* ── LIGHT THEME ── */
:root{
  --navy:#0f1f3d;
  --navy-light:#162847;
  --amber:#f59e0b;
  --amber-light:#fbbf24;

  --bg:#ffffff;
  --bg-alt:#f8f9fb;
  --surface:#ffffff;
  --text:#1e293b;
  --muted:#64748b;
  --border:#e2e8f0;
  --card-bg:#ffffff;
  --card-border:#e2e8f0;
  --header-bg:rgba(255,255,255,0.96);
  --stat-bg:#f8f9fb;
  --section-title-color:#0f1f3d;
  --nav-link-color:#64748b;
  --nav-link-hover:#0f1f3d;
  --toggle-bg:#e2e8f0;
  --toggle-icon-color:#64748b;
  --progress-bar-bg:#e2e8f0;
  --footer-bg:#0a172e;
  --footer-text:rgba(255,255,255,0.4);
}

/* ── DARK THEME ── */
[data-theme="dark"]{
  --bg:#0d1117;
  --bg-alt:#161b22;
  --surface:#161b22;
  --text:#e6edf3;
  --muted:#8b949e;
  --border:#30363d;
  --card-bg:#1c2128;
  --card-border:#30363d;
  --header-bg:rgba(13,17,23,0.96);
  --stat-bg:#1c2128;
  --section-title-color:#e6edf3;
  --nav-link-color:#8b949e;
  --nav-link-hover:#e6edf3;
  --toggle-bg:#30363d;
  --toggle-icon-color:#f59e0b;
  --progress-bar-bg:#30363d;
  --footer-bg:#010409;
  --footer-text:rgba(255,255,255,0.3);
}

/* ── BASE ── */
html{scroll-behavior:smooth;}
body{
  font-family:'Outfit',sans-serif;
  color:var(--text);
  background:var(--bg);
  line-height:1.6;
  transition:background 0.3s,color 0.3s;
}

/* ── SCROLL PROGRESS BAR ── */
#scroll-progress{
  position:fixed;top:0;left:0;height:3px;width:0%;
  background:linear-gradient(90deg,var(--amber),var(--amber-light));
  z-index:9999;transition:width 0.1s linear;
}

/* ── BACK TO TOP ── */
#back-top{
  position:fixed;bottom:2rem;right:2rem;z-index:500;
  width:44px;height:44px;border-radius:50%;
  background:var(--amber);color:var(--navy);
  border:none;cursor:pointer;font-size:1rem;
  display:flex;align-items:center;justify-content:center;
  opacity:0;transform:translateY(12px);
  transition:opacity 0.3s,transform 0.3s;
  box-shadow:0 4px 16px rgba(245,158,11,0.4);
}
#back-top.visible{opacity:1;transform:translateY(0);}
#back-top:hover{background:var(--amber-light);}

/* ── HEADER ── */
header{
  position:sticky;top:0;z-index:100;
  background:var(--header-bg);
  backdrop-filter:blur(12px);
  border-bottom:1px solid var(--border);
  padding:0 2rem;
  transition:background 0.3s,border-color 0.3s;
}
nav{max-width:1100px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;height:64px;}
.logo{font-family:'Sora',sans-serif;font-weight:700;font-size:1.2rem;color:var(--section-title-color);}
.logo span{color:var(--amber);}
.nav-links{display:flex;gap:2rem;list-style:none;align-items:center;}
.nav-links a{
  text-decoration:none;color:var(--nav-link-color);
  font-size:0.9rem;font-weight:500;
  transition:color 0.2s;position:relative;
}
.nav-links a:not(.btn-contact)::after{
  content:'';position:absolute;bottom:-4px;left:0;
  width:0;height:2px;background:var(--amber);
  transition:width 0.25s;border-radius:1px;
}
.nav-links a:not(.btn-contact):hover::after{width:100%;}
.nav-links a:hover{color:var(--nav-link-hover);}
.nav-links .btn-contact{
  background:var(--navy);color:#fff!important;
  padding:0.5rem 1.2rem;border-radius:6px;
  transition:background 0.2s!important;
}
.nav-links .btn-contact:hover{background:var(--amber)!important;color:var(--navy)!important;}
[data-theme="dark"] .nav-links .btn-contact{background:var(--amber);color:var(--navy)!important;}
[data-theme="dark"] .nav-links .btn-contact:hover{background:var(--amber-light)!important;}

/* ── DARK MODE TOGGLE ── */
.theme-toggle{
  background:var(--toggle-bg);border:none;
  width:38px;height:38px;border-radius:50%;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  color:var(--toggle-icon-color);font-size:1rem;
  transition:background 0.3s,color 0.3s;
  flex-shrink:0;
}
.theme-toggle:hover{background:var(--amber);color:var(--navy);}

/* ── HERO ── */
.hero{background:var(--navy);color:#fff;padding:6rem 2rem 5rem;position:relative;overflow:hidden;}
.hero::before{content:'';position:absolute;top:-40%;right:-10%;width:600px;height:600px;background:radial-gradient(circle,rgba(245,158,11,0.13) 0%,transparent 70%);pointer-events:none;}
[data-theme="dark"] .hero{background:#0d1117;border-bottom:1px solid var(--border);}
.hero-inner{max-width:1100px;margin:0 auto;}
.hero-badge{display:inline-flex;align-items:center;gap:0.5rem;background:rgba(245,158,11,0.15);border:1px solid rgba(245,158,11,0.3);color:var(--amber-light);padding:0.4rem 1rem;border-radius:999px;font-size:0.8rem;font-weight:500;margin-bottom:1.5rem;}
.hero h1{font-family:'Sora',sans-serif;font-size:clamp(2rem,5vw,3.2rem);font-weight:700;line-height:1.15;margin-bottom:1rem;}
.hero h1 .highlight{color:var(--amber);}
.hero p{font-size:1.05rem;color:rgba(255,255,255,0.7);max-width:540px;margin-bottom:2rem;line-height:1.7;}
.hero-btns{display:flex;flex-wrap:wrap;gap:1rem;}
.btn-primary{background:var(--amber);color:var(--navy);padding:0.75rem 1.75rem;border-radius:8px;text-decoration:none;font-weight:600;font-size:0.95rem;transition:transform 0.2s,background 0.2s;}
.btn-primary:hover{background:var(--amber-light);transform:translateY(-2px);}
.btn-secondary{background:transparent;color:#fff;padding:0.75rem 1.75rem;border-radius:8px;text-decoration:none;font-weight:500;font-size:0.95rem;border:1px solid rgba(255,255,255,0.3);transition:border-color 0.2s,background 0.2s;}
.btn-secondary:hover{border-color:var(--amber);background:rgba(245,158,11,0.1);}

/* ── SECTIONS ── */
section{padding:5rem 2rem;}
.section-inner{max-width:1100px;margin:0 auto;}
.section-label{text-transform:uppercase;letter-spacing:0.1em;font-size:0.75rem;font-weight:600;color:var(--amber);margin-bottom:0.5rem;}
.section-title{font-family:'Sora',sans-serif;font-size:clamp(1.6rem,3vw,2.2rem);font-weight:700;color:var(--section-title-color);margin-bottom:1rem;transition:color 0.3s;}
.section-line{width:48px;height:3px;background:var(--amber);border-radius:2px;margin-bottom:2.5rem;}

/* ── SCROLL REVEAL ── */
.reveal{opacity:0;transform:translateY(28px);transition:opacity 0.6s ease,transform 0.6s ease;}
.reveal.visible{opacity:1;transform:translateY(0);}
.reveal-delay-1{transition-delay:0.1s;}
.reveal-delay-2{transition-delay:0.2s;}
.reveal-delay-3{transition-delay:0.3s;}

/* ── HERO SOCIALS ── */
.hero-socials{margin-top:2.5rem;padding-top:2rem;border-top:1px solid rgba(255,255,255,0.12);}
.hero-socials-label{font-size:0.75rem;font-weight:600;text-transform:uppercase;letter-spacing:0.1em;color:rgba(255,255,255,0.4);margin-bottom:1rem;}
.hero-socials-row{display:flex;flex-wrap:wrap;gap:0.75rem;}
.hsoc-btn{display:inline-flex;align-items:center;gap:0.5rem;padding:0.6rem 1.1rem;border-radius:8px;font-size:0.85rem;font-weight:600;text-decoration:none;transition:transform 0.2s,opacity 0.2s;border:none;}
.hsoc-btn:hover{transform:translateY(-2px);opacity:0.88;}
.hsoc-btn svg{width:18px;height:18px;flex-shrink:0;}
.hsoc-linkedin{background:#0a66c2;color:#fff;}
.hsoc-instagram{background:linear-gradient(135deg,#f9ce34,#ee2a7b,#6228d7);color:#fff;}
.hsoc-tiktok{background:#010101;color:#fff;border:1px solid rgba(255,255,255,0.15);}
.hsoc-github{background:#24292f;color:#fff;border:1px solid rgba(255,255,255,0.15);}
.hsoc-github:hover{background:#3c4147;}

/* ── ABOUT ── */
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:3rem;align-items:center;}
.about-text p{color:var(--muted);font-size:1rem;line-height:1.8;margin-bottom:1rem;}
.stats-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem;}
.stat-card{background:var(--stat-bg);border-radius:12px;padding:1.25rem;border-left:3px solid var(--amber);transition:background 0.3s;}
.stat-card .stat-num{font-family:'Sora',sans-serif;font-size:1.6rem;font-weight:700;color:var(--section-title-color);}
.stat-card .stat-label{font-size:0.8rem;color:var(--muted);margin-top:0.2rem;}

/* ── SKILLS ── */
.skills-bg{background:var(--bg-alt);transition:background 0.3s;}
.skills-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:1.25rem;}
.skill-card{background:var(--card-bg);border-radius:12px;padding:1.5rem;border:1px solid var(--card-border);transition:border-color 0.2s,transform 0.2s,background 0.3s;}
.skill-card:hover{border-color:var(--amber);transform:translateY(-3px);}
.skill-icon{width:44px;height:44px;background:rgba(245,158,11,0.1);border-radius:10px;display:flex;align-items:center;justify-content:center;margin-bottom:1rem;}
.skill-icon i{color:var(--amber);font-size:1.2rem;}
.skill-card h3{font-family:'Sora',sans-serif;font-size:1rem;font-weight:600;color:var(--section-title-color);margin-bottom:0.5rem;}
.skill-card p{font-size:0.88rem;color:var(--muted);line-height:1.6;}

/* ── SKILL BARS ── */
.skill-bar-list{margin-top:2rem;display:flex;flex-direction:column;gap:1.1rem;}
.skill-bar-item{}
.skill-bar-label{display:flex;justify-content:space-between;font-size:0.85rem;font-weight:500;color:var(--text);margin-bottom:0.35rem;}
.skill-bar-track{background:var(--progress-bar-bg);border-radius:999px;height:7px;overflow:hidden;}
.skill-bar-fill{height:100%;border-radius:999px;background:linear-gradient(90deg,var(--amber),var(--amber-light));width:0;transition:width 1s ease;}

/* ── PROJECTS ── */
.projects-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:1.5rem;}
.project-card{background:var(--card-bg);border-radius:14px;padding:1.75rem;border:1px solid var(--card-border);transition:box-shadow 0.2s,transform 0.2s,background 0.3s,border-color 0.3s;}
.project-card:hover{box-shadow:0 8px 32px rgba(0,0,0,0.12);transform:translateY(-3px);}
.project-tag{display:inline-block;background:rgba(245,158,11,0.12);color:#92400e;padding:0.25rem 0.75rem;border-radius:999px;font-size:0.75rem;font-weight:600;margin-bottom:1rem;}
[data-theme="dark"] .project-tag{color:var(--amber-light);}
.project-card h3{font-family:'Sora',sans-serif;font-size:1.1rem;font-weight:600;color:var(--section-title-color);margin-bottom:0.6rem;}
.project-card p{font-size:0.9rem;color:var(--muted);line-height:1.7;}

/* ── CONTACT ── */
.contact-bg{background:var(--navy);}
[data-theme="dark"] .contact-bg{background:#010409;border-top:1px solid var(--border);}
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:start;}
.contact-info .section-title{color:#fff;}
.contact-info p{color:rgba(255,255,255,0.65);margin-bottom:2rem;line-height:1.7;}
.info-item{display:flex;align-items:center;gap:0.75rem;margin-bottom:1rem;color:rgba(255,255,255,0.8);font-size:0.95rem;}
.info-item i{color:var(--amber);width:18px;}
.social-row{display:flex;gap:1rem;margin-top:1.5rem;}
.social-btn{width:40px;height:40px;border-radius:8px;border:1px solid rgba(255,255,255,0.2);display:flex;align-items:center;justify-content:center;color:rgba(255,255,255,0.7);text-decoration:none;font-size:1rem;transition:border-color 0.2s,color 0.2s;}
.social-btn:hover{border-color:var(--amber);color:var(--amber);}
.contact-actions{display:flex;flex-direction:column;gap:1rem;padding-top:1rem;}
.btn-cta{display:flex;align-items:center;justify-content:center;gap:0.75rem;padding:0.9rem 1.5rem;border-radius:10px;text-decoration:none;font-weight:600;font-size:0.95rem;transition:transform 0.2s,opacity 0.2s;}
.btn-cta:hover{transform:translateY(-2px);opacity:0.9;}
.btn-email{background:var(--amber);color:var(--navy);}
.btn-whatsapp{background:#25d366;color:#fff;}
.cta-note{color:rgba(255,255,255,0.4);font-size:0.8rem;text-align:center;margin-top:0.5rem;}

/* ── ACTIVE NAV LINK ── */
.nav-links a.active{color:var(--amber);}

/* ── FOOTER ── */
footer{background:var(--footer-bg);color:var(--footer-text);text-align:center;padding:1.5rem;font-size:0.85rem;transition:background 0.3s;}
footer span{color:var(--amber);}

/* ── MOBILE ── */
@media(max-width:768px){
  .about-grid,.contact-grid{grid-template-columns:1fr;}
  .stats-grid{grid-template-columns:1fr 1fr;}
  .nav-links{display:none;}
  #back-top{bottom:1.25rem;right:1.25rem;}
}
</style>
</head>
<body>

<!-- Scroll progress bar -->
<div id="scroll-progress"></div>

<!-- Back to top button -->
<button id="back-top" aria-label="Back to top" onclick="window.scrollTo({top:0,behavior:'smooth'})">
  <i class="fas fa-arrow-up"></i>
</button>

<header>
  <nav>
    <div class="logo">Martin<span>.</span></div>
    <ul class="nav-links" id="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact" class="btn-contact">Contact Me</a></li>
    </ul>
    <button class="theme-toggle" id="theme-toggle" aria-label="Toggle dark mode">
      <i class="fas fa-moon" id="theme-icon"></i>
    </button>
  </nav>
</header>

<section class="hero" id="home">
  <div class="hero-inner">
    <div class="hero-badge"><i class="fas fa-circle-dot fa-xs"></i> Available for Industrial Attachment — May–July 2026</div>
    <h1>Hi, I'm <span class="highlight">Martin Karani</span>,<br>IT Specialist &amp; Developer</h1>
    <p>Diploma in IT student at KCA University with hands-on skills in system administration, Python automation, and hardware support. Based in Nairobi, Kenya.</p>
    <div class="hero-btns">
      <a href="#projects" class="btn-primary">View My Work</a>
      <a href="MARTIN_MURIMI_KARANI_CV.pdf" download="MARTIN_MURIMI_KARANI_CV.pdf" class="btn-secondary">Download CV <i class="fas fa-download" style="margin-left:6px;font-size:0.85em;"></i></a>
    </div>

    <!-- Social Links -->
    <div class="hero-socials reveal">
      <p class="hero-socials-label">Connect with me</p>
      <div class="hero-socials-row">
        <a href="https://www.linkedin.com/in/martin-karani-b6a310268" target="_blank" rel="noopener noreferrer" class="hsoc-btn hsoc-linkedin">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
          LinkedIn
        </a>
        <a href="https://www.instagram.com/user_mkm71?igsh=amRkZjhwbjQ2N2Rn" target="_blank" rel="noopener noreferrer" class="hsoc-btn hsoc-instagram">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
          Instagram
        </a>
        <a href="https://www.tiktok.com/@_.mkm71?_r=1&_t=ZS=97fbsGtkuxv" target="_blank" rel="noopener noreferrer" class="hsoc-btn hsoc-tiktok">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.02 1.73 4.12 1.13 1.09 2.66 1.63 4.21 1.63v3.94c-1.42-.01-2.83-.45-4.01-1.25-.79-.53-1.44-1.24-1.92-2.06v7.1c.04 4.09-2.54 7.82-6.52 8.78-4.04.98-8.38-1.23-9.58-5.18-1.23-4.01.83-8.47 4.75-9.87 1.34-.48 2.78-.54 4.15-.17v3.94c-1.07-.33-2.25-.11-3.12.57-.94.71-1.39 1.92-1.12 3.09.28 1.18 1.31 2.05 2.53 2.08 1.48.06 2.77-1.04 2.92-2.51.02-.21.03-.42.03-.64V0c-.01.01-.01.01 0 .02z"/></svg>
          TikTok
        </a>
        <a href="https://github.com/karanihmartoh-svg" target="_blank" rel="noopener noreferrer" class="hsoc-btn hsoc-github">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
          GitHub
        </a>
      </div>
    </div>
  </div>
</section>

<section id="about">
  <div class="section-inner">
    <div class="about-grid">
      <div class="about-text reveal">
        <div class="section-label">About Me</div>
        <h2 class="section-title">A Dedicated IT Student Ready to Contribute</h2>
        <div class="section-line"></div>
        <p>I'm a focused IT student with a strong foundation in system administration and software development. I'm passionate about using Python and JavaScript to solve real hardware and software challenges.</p>
        <p>Currently seeking an Industrial Attachment placement (May – July 2026) in Nairobi where I can apply my skills and grow in a professional environment.</p>
      </div>
      <div class="stats-grid reveal reveal-delay-1">
        <div class="stat-card">
          <div class="stat-num">2.77</div>
          <div class="stat-label">Current GPA at KCA University</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">B+</div>
          <div class="stat-label">Desktop Photography &amp; Video Editing</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">B</div>
          <div class="stat-label">Computer Support &amp; Maintenance</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">2026</div>
          <div class="stat-label">Available for Attachment — Nairobi</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="skills" class="skills-bg">
  <div class="section-inner">
    <div class="section-label">What I Do</div>
    <h2 class="section-title">Technical Skills</h2>
    <div class="section-line"></div>
    <div class="skills-grid">
      <div class="skill-card reveal">
        <div class="skill-icon"><i class="fas fa-tools"></i></div>
        <h3>Hardware &amp; Support</h3>
        <p>PC assembly, troubleshooting, and OS configuration. Specialised in RAM management and smart system updates for Android and VIDAA platforms.</p>
      </div>
      <div class="skill-card reveal reveal-delay-1">
        <div class="skill-icon"><i class="fas fa-code"></i></div>
        <h3>Development</h3>
        <p>Proficient in Python automation and JavaScript. Experienced using VS Code for efficient script development and web projects.</p>
      </div>
      <div class="skill-card reveal reveal-delay-2">
        <div class="skill-icon"><i class="fas fa-video"></i></div>
        <h3>Digital Media</h3>
        <p>Advanced skills in desktop photography and video editing, useful for technical documentation and content creation.</p>
      </div>
      <div class="skill-card reveal reveal-delay-3">
        <div class="skill-icon"><i class="fas fa-network-wired"></i></div>
        <h3>System Administration</h3>
        <p>Fundamentals of network configuration, organisational IT management, and enterprise environment support.</p>
      </div>
    </div>

    <!-- Skill proficiency bars -->
    <div class="skill-bar-list reveal" style="max-width:560px;margin-top:3rem;">
      <div class="section-label" style="margin-bottom:1rem;">Proficiency levels</div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Python</span><span>75%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-width="75"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>JavaScript</span><span>65%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-width="65"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Hardware Support</span><span>85%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Video Editing</span><span>80%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-width="80"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Network Config</span><span>60%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-width="60"></div></div>
      </div>
    </div>
  </div>
</section>

<section id="projects">
  <div class="section-inner">
    <div class="section-label">My Work</div>
    <h2 class="section-title">Featured Projects</h2>
    <div class="section-line"></div>
    <div class="projects-grid">
      <div class="project-card reveal">
        <span class="project-tag">System Optimisation</span>
        <h3>Smart TV System Optimisation</h3>
        <p>Configured and optimised OS and RAM settings for high-performance smart television systems, ensuring smooth firmware updates and long-term hardware stability.</p>
      </div>
      <div class="project-card reveal reveal-delay-1">
        <span class="project-tag">KCA University</span>
        <h3>DIT 503 Capstone Project</h3>
        <p>Completed a comprehensive IT capstone project demonstrating practical application of system design principles, including analysis, planning, and implementation phases.</p>
      </div>
      <div class="project-card reveal reveal-delay-2">
        <span class="project-tag">Web Development</span>
        <h3>Personal Portfolio Website</h3>
        <p>Designed and built this responsive portfolio from scratch using HTML, CSS, and JavaScript to showcase skills and attract Industrial Attachment opportunities.</p>
      </div>
    </div>
  </div>
</section>

<section id="contact" class="contact-bg">
  <div class="section-inner">
    <div class="contact-grid">
      <div class="contact-info reveal">
        <div class="section-label">Get In Touch</div>
        <h2 class="section-title">Let's Connect</h2>
        <div class="section-line"></div>
        <p>I'm available for an Industrial Attachment for the <strong style="color:var(--amber-light);">May – July 2026</strong> intake. Feel free to reach out via email or WhatsApp.</p>
        <div class="info-item"><i class="fas fa-envelope"></i> karanihmartoh@gmail.com</div>
        <div class="info-item"><i class="fas fa-phone"></i> +254 792 429 733</div>
        <div class="info-item"><i class="fas fa-map-marker-alt"></i> Nairobi, Kenya (Zimmerman/Ruaraka)</div>
        <div class="social-row">
          <a href="https://github.com/karanihmartoh-svg" target="_blank" rel="noopener noreferrer" class="social-btn" aria-label="GitHub"><i class="fab fa-github"></i></a>
          <a href="#" class="social-btn" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
        </div>
      </div>
      <div class="reveal reveal-delay-1">
        <div class="contact-actions">
          <a href="mailto:karanihmartoh@gmail.com?subject=Industrial%20Attachment%20Inquiry" class="btn-cta btn-email">
            <i class="fas fa-envelope"></i> Email Me Directly
          </a>
          <a href="https://wa.me/254792429733?text=Hi%20Martin,%20I'm%20contacting%20you%20from%20your%20IT%20Portfolio!" target="_blank" class="btn-cta btn-whatsapp">
            <i class="fab fa-whatsapp"></i> Chat on WhatsApp
          </a>
          <p class="cta-note">Usually responds within 24 hours</p>
        </div>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 <span>Martin Karani</span> · Nairobi, Kenya · Built with HTML, CSS &amp; JavaScript</p>
</footer>

<script>
// ── DARK MODE ──
const html = document.documentElement;
const toggleBtn = document.getElementById('theme-toggle');
const themeIcon = document.getElementById('theme-icon');

function applyTheme(theme){
  html.setAttribute('data-theme', theme);
  themeIcon.className = theme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
  localStorage.setItem('theme', theme);
}

// Load saved preference or system preference
const saved = localStorage.getItem('theme');
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
applyTheme(saved || (prefersDark ? 'dark' : 'light'));

toggleBtn.addEventListener('click', () => {
  applyTheme(html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
});

// ── SCROLL PROGRESS BAR ──
const bar = document.getElementById('scroll-progress');
window.addEventListener('scroll', () => {
  const scrolled = window.scrollY;
  const total = document.documentElement.scrollHeight - window.innerHeight;
  bar.style.width = (scrolled / total * 100) + '%';
}, {passive: true});

// ── BACK TO TOP BUTTON ──
const backTop = document.getElementById('back-top');
window.addEventListener('scroll', () => {
  backTop.classList.toggle('visible', window.scrollY > 400);
}, {passive: true});

// ── SCROLL REVEAL ──
const revealEls = document.querySelectorAll('.reveal');
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('visible'); });
}, {threshold: 0.15});
revealEls.forEach(el => revealObserver.observe(el));

// ── SKILL BARS ──
const barFills = document.querySelectorAll('.skill-bar-fill');
const barObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if(e.isIntersecting){
      e.target.style.width = e.target.dataset.width + '%';
      barObserver.unobserve(e.target);
    }
  });
}, {threshold: 0.3});
barFills.forEach(el => barObserver.observe(el));

// ── ACTIVE NAV LINK ON SCROLL ──
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a[href^="#"]');
const navObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if(e.isIntersecting){
      navLinks.forEach(a => a.classList.remove('active'));
      const active = document.querySelector(`.nav-links a[href="#${e.target.id}"]`);
      if(active) active.classList.add('active');
    }
  });
}, {threshold: 0.4});
sections.forEach(s => navObserver.observe(s));

// ── SMOOTH SCROLL FOR NAV LINKS ──
navLinks.forEach(link => {
  link.addEventListener('click', e => {
    const target = document.querySelector(link.getAttribute('href'));
    if(target){
      e.preventDefault();
      target.scrollIntoView({behavior:'smooth', block:'start'});
    }
  });
});
</script>
</body>
</html>
