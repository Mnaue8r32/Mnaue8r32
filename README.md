<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Juan Manuel Cruz Beltrán — Full Stack Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #080b10;
  --surface: #0d1117;
  --surface2: #141b24;
  --border: #1e2d3d;
  --border2: #263344;
  --accent: #00d9ff;
  --accent2: #7b61ff;
  --accent3: #00ff88;
  --text: #e8edf2;
  --text2: #8b9cb0;
  --text3: #4a5a6a;
  --red: #ff4d6a;
  --orange: #ff8c42;
  --font-display: 'Syne', sans-serif;
  --font-mono: 'Space Mono', monospace;
  --font-body: 'DM Sans', sans-serif;
  --glow: 0 0 40px rgba(0,217,255,0.15);
  --glow2: 0 0 40px rgba(123,97,255,0.15);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.6;
  overflow-x: hidden;
}

/* ── NOISE OVERLAY ── */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: 0.4;
}

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 2px; }

/* ── NAV ── */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 3rem;
  height: 64px;
  background: rgba(8,11,16,0.85);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
}

.nav-logo {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--accent);
  letter-spacing: 0.05em;
}
.nav-logo span { color: var(--text3); }

.nav-links {
  display: flex;
  gap: 2rem;
  list-style: none;
}
.nav-links a {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--text2);
  text-decoration: none;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  transition: color 0.2s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0; right: 0;
  height: 1px;
  background: var(--accent);
  transform: scaleX(0);
  transition: transform 0.2s;
}
.nav-links a:hover { color: var(--accent); }
.nav-links a:hover::after { transform: scaleX(1); }

.nav-status {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--accent3);
}
.status-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--accent3);
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%,100% { opacity: 1; box-shadow: 0 0 0 0 rgba(0,255,136,0.4); }
  50% { opacity: 0.7; box-shadow: 0 0 0 6px rgba(0,255,136,0); }
}

/* ── HERO ── */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding: 0 3rem;
}

.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(0,217,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,217,255,0.03) 1px, transparent 1px);
  background-size: 80px 80px;
  mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 20%, transparent 100%);
}

.hero-glow {
  position: absolute;
  top: 20%; left: 10%;
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(0,217,255,0.06) 0%, transparent 70%);
  pointer-events: none;
}
.hero-glow2 {
  position: absolute;
  bottom: 10%; right: 5%;
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(123,97,255,0.08) 0%, transparent 70%);
  pointer-events: none;
}

.hero-content {
  position: relative;
  z-index: 1;
  max-width: 900px;
}

.hero-tag {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--accent);
  border: 1px solid rgba(0,217,255,0.3);
  padding: 0.35rem 0.9rem;
  border-radius: 2px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 2.5rem;
  background: rgba(0,217,255,0.04);
}

.hero-name {
  font-family: var(--font-display);
  font-size: clamp(3.5rem, 9vw, 8rem);
  font-weight: 800;
  line-height: 0.9;
  letter-spacing: -0.03em;
  margin-bottom: 0.3em;
}
.hero-name .first { color: var(--text); display: block; }
.hero-name .last {
  color: transparent;
  -webkit-text-stroke: 1px rgba(255,255,255,0.15);
  display: block;
}

.hero-title {
  font-family: var(--font-mono);
  font-size: 1rem;
  color: var(--accent);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  margin-bottom: 1.5rem;
}

.hero-desc {
  font-size: 1.1rem;
  color: var(--text2);
  max-width: 560px;
  line-height: 1.7;
  margin-bottom: 3rem;
  font-weight: 300;
}

.hero-ctas {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  align-items: center;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  background: var(--accent);
  color: var(--bg);
  font-family: var(--font-mono);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-decoration: none;
  padding: 0.85rem 2rem;
  border-radius: 2px;
  transition: all 0.2s;
}
.btn-primary:hover {
  background: #00b8d9;
  transform: translateY(-1px);
  box-shadow: 0 8px 30px rgba(0,217,255,0.3);
}

.btn-ghost {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  background: transparent;
  color: var(--text2);
  font-family: var(--font-mono);
  font-size: 0.78rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-decoration: none;
  padding: 0.85rem 2rem;
  border: 1px solid var(--border2);
  border-radius: 2px;
  transition: all 0.2s;
}
.btn-ghost:hover {
  border-color: var(--accent);
  color: var(--accent);
  background: rgba(0,217,255,0.05);
}

.hero-scroll {
  position: absolute;
  bottom: 2.5rem;
  left: 3rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.scroll-line {
  width: 60px; height: 1px;
  background: linear-gradient(90deg, var(--text3), transparent);
  animation: scrollLine 2s infinite;
}
@keyframes scrollLine {
  0% { width: 0; opacity: 0; }
  50% { width: 60px; opacity: 1; }
  100% { width: 60px; opacity: 0; }
}

.hero-stats {
  position: absolute;
  right: 3rem;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.stat-item {
  text-align: right;
}
.stat-value {
  font-family: var(--font-display);
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--text);
  line-height: 1;
}
.stat-value span { color: var(--accent); }
.stat-label {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-top: 0.25rem;
}

/* ── SECTION BASE ── */
section {
  padding: 8rem 3rem;
  position: relative;
}
.section-inner { max-width: 1200px; margin: 0 auto; }

.section-label {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  color: var(--accent);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}
.section-label::before {
  content: '';
  width: 30px; height: 1px;
  background: var(--accent);
}

.section-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 800;
  line-height: 1.05;
  letter-spacing: -0.02em;
  margin-bottom: 1rem;
}
.section-title .accent { color: var(--accent); }

/* ── ABOUT ── */
#about { background: var(--surface); }

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: start;
}

.about-text p {
  color: var(--text2);
  font-size: 1.05rem;
  font-weight: 300;
  margin-bottom: 1.25rem;
  line-height: 1.8;
}
.about-text p strong { color: var(--text); font-weight: 500; }

.about-right { display: flex; flex-direction: column; gap: 2rem; }

.code-block {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 4px;
  overflow: hidden;
}
.code-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  border-bottom: 1px solid var(--border);
  background: var(--surface2);
}
.code-dot {
  width: 10px; height: 10px;
  border-radius: 50%;
}
.code-dot.red { background: var(--red); }
.code-dot.orange { background: var(--orange); }
.code-dot.green { background: var(--accent3); }
.code-filename {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  color: var(--text3);
  margin-left: auto;
  letter-spacing: 0.05em;
}
.code-body {
  padding: 1.5rem;
  font-family: var(--font-mono);
  font-size: 0.78rem;
  line-height: 1.8;
  color: var(--text2);
}
.code-kw { color: var(--accent2); }
.code-str { color: var(--accent3); }
.code-key { color: var(--accent); }
.code-num { color: var(--orange); }
.code-cmt { color: var(--text3); }

.about-stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: var(--border);
  border: 1px solid var(--border);
  border-radius: 4px;
  overflow: hidden;
}
.stat-block {
  background: var(--bg);
  padding: 1.5rem;
  text-align: center;
}
.stat-block .val {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 800;
  color: var(--accent);
}
.stat-block .lbl {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  color: var(--text3);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-top: 0.3rem;
}

/* ── TECH STACK ── */
#tech { background: var(--bg); }

.tech-categories {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2px;
  background: var(--border);
  border: 1px solid var(--border);
  border-radius: 4px;
  overflow: hidden;
  margin-top: 4rem;
}

.tech-cat {
  background: var(--surface);
  padding: 2.5rem;
  position: relative;
  transition: background 0.3s;
}
.tech-cat:hover { background: var(--surface2); }

.tech-cat-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}
.tech-cat-icon {
  width: 36px; height: 36px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
}
.tech-cat-icon.be { background: rgba(0,217,255,0.1); }
.tech-cat-icon.fe { background: rgba(123,97,255,0.1); }
.tech-cat-icon.mo { background: rgba(0,255,136,0.1); }
.tech-cat-icon.db { background: rgba(255,140,66,0.1); }

.tech-cat-title {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--text2);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.tech-pills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}
.tech-pill {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  padding: 0.35rem 0.8rem;
  border-radius: 2px;
  border: 1px solid;
  transition: all 0.2s;
  letter-spacing: 0.03em;
}
.tech-pill.be { border-color: rgba(0,217,255,0.2); color: var(--accent); background: rgba(0,217,255,0.04); }
.tech-pill.fe { border-color: rgba(123,97,255,0.2); color: var(--accent2); background: rgba(123,97,255,0.04); }
.tech-pill.mo { border-color: rgba(0,255,136,0.2); color: var(--accent3); background: rgba(0,255,136,0.04); }
.tech-pill.db { border-color: rgba(255,140,66,0.2); color: var(--orange); background: rgba(255,140,66,0.04); }
.tech-pill:hover { transform: translateY(-1px); }

/* ── SKILLS ── */
#skills { background: var(--surface); }

.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-top: 4rem;
}

.skill-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 2rem;
  position: relative;
  overflow: hidden;
  transition: border-color 0.3s, transform 0.3s;
}
.skill-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
}
.skill-card.arch::before { background: linear-gradient(90deg, var(--accent), transparent); }
.skill-card.eng::before { background: linear-gradient(90deg, var(--accent2), transparent); }
.skill-card.soft::before { background: linear-gradient(90deg, var(--accent3), transparent); }

.skill-card:hover {
  border-color: var(--border2);
  transform: translateY(-3px);
}

.skill-card-icon {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}
.skill-card-title {
  font-family: var(--font-display);
  font-size: 1rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 1.25rem;
}
.skill-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
.skill-list li {
  font-size: 0.85rem;
  color: var(--text2);
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-weight: 300;
}
.skill-list li::before {
  content: '';
  width: 4px; height: 4px;
  border-radius: 50%;
  flex-shrink: 0;
}
.arch .skill-list li::before { background: var(--accent); }
.eng .skill-list li::before { background: var(--accent2); }
.soft .skill-list li::before { background: var(--accent3); }

/* ── PROJECTS ── */
#projects { background: var(--bg); }

.projects-header {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 4rem;
  gap: 2rem;
}
.projects-subtitle {
  font-size: 0.95rem;
  color: var(--text2);
  max-width: 450px;
  font-weight: 300;
  line-height: 1.7;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-auto-rows: auto;
  gap: 1.5rem;
}

.proj-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 2.5rem;
  position: relative;
  overflow: hidden;
  transition: border-color 0.3s, transform 0.3s;
  display: flex;
  flex-direction: column;
}
.proj-card:hover {
  border-color: var(--border2);
  transform: translateY(-2px);
}
.proj-card:hover .proj-arrow { transform: translate(3px, -3px); opacity: 1; }

.proj-card.featured { grid-column: span 7; }
.proj-card.regular { grid-column: span 5; }
.proj-card.wide { grid-column: span 12; }
.proj-card.half { grid-column: span 6; }

.proj-card-top {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 1.5rem;
}
.proj-type-badge {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 0.3rem 0.7rem;
  border-radius: 2px;
  border: 1px solid;
}
.badge-fs { border-color: rgba(0,217,255,0.3); color: var(--accent); background: rgba(0,217,255,0.05); }
.badge-be { border-color: rgba(123,97,255,0.3); color: var(--accent2); background: rgba(123,97,255,0.05); }
.badge-fe { border-color: rgba(0,255,136,0.3); color: var(--accent3); background: rgba(0,255,136,0.05); }

.proj-arrow {
  color: var(--text3);
  font-size: 1.1rem;
  opacity: 0.5;
  transition: all 0.3s;
  text-decoration: none;
}

.proj-title {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.75rem;
  letter-spacing: -0.01em;
  line-height: 1.2;
}

.proj-desc {
  font-size: 0.9rem;
  color: var(--text2);
  line-height: 1.7;
  margin-bottom: 1.5rem;
  font-weight: 300;
  flex: 1;
}

.proj-highlights {
  list-style: none;
  margin-bottom: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.proj-highlights li {
  font-size: 0.8rem;
  color: var(--text2);
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
}
.proj-highlights li::before {
  content: '›';
  color: var(--accent);
  font-weight: 700;
  flex-shrink: 0;
  margin-top: -1px;
}

.proj-techs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}
.proj-tech {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  padding: 0.2rem 0.5rem;
  background: var(--surface2);
  border-radius: 2px;
  letter-spacing: 0.03em;
}

/* ── EXPERIENCE ── */
#experience { background: var(--surface); }

.exp-timeline {
  position: relative;
  margin-top: 4rem;
  padding-left: 2rem;
}
.exp-timeline::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 1px;
  background: linear-gradient(180deg, var(--accent), var(--accent2), transparent);
}

.exp-item {
  position: relative;
  padding: 0 0 4rem 3rem;
}
.exp-item:last-child { padding-bottom: 0; }

.exp-dot {
  position: absolute;
  left: -5px; top: 6px;
  width: 10px; height: 10px;
  border-radius: 50%;
  background: var(--accent);
  border: 2px solid var(--bg);
  box-shadow: 0 0 0 3px rgba(0,217,255,0.2);
}
.exp-item:nth-child(2) .exp-dot { background: var(--accent2); box-shadow: 0 0 0 3px rgba(123,97,255,0.2); }
.exp-item:nth-child(3) .exp-dot { background: var(--accent3); box-shadow: 0 0 0 3px rgba(0,255,136,0.2); }
.exp-item:nth-child(4) .exp-dot { background: var(--text3); box-shadow: 0 0 0 3px rgba(74,90,106,0.2); }

.exp-meta {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 0.75rem;
}
.exp-period {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--accent);
  letter-spacing: 0.05em;
}
.exp-item:nth-child(2) .exp-period { color: var(--accent2); }
.exp-item:nth-child(3) .exp-period { color: var(--accent3); }

.exp-title-text {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.75rem;
}
.exp-desc {
  font-size: 0.9rem;
  color: var(--text2);
  line-height: 1.8;
  font-weight: 300;
  max-width: 720px;
  margin-bottom: 1.25rem;
}
.exp-techs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}
.exp-tech {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  padding: 0.2rem 0.5rem;
  border: 1px solid var(--border);
  border-radius: 2px;
  letter-spacing: 0.03em;
}

/* ── CONTACT ── */
#contact { background: var(--bg); }

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: start;
  margin-top: 4rem;
}

.contact-left p {
  font-size: 1.05rem;
  color: var(--text2);
  font-weight: 300;
  line-height: 1.8;
  margin-bottom: 3rem;
}

.contact-links {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.contact-link {
  display: flex;
  align-items: center;
  gap: 1rem;
  text-decoration: none;
  padding: 1.25rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 4px;
  background: var(--surface);
  transition: all 0.2s;
  group: true;
}
.contact-link:hover {
  border-color: var(--accent);
  background: rgba(0,217,255,0.04);
  transform: translateX(4px);
}
.contact-link-icon {
  width: 40px; height: 40px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.1rem;
  flex-shrink: 0;
}
.contact-link-icon.gh { background: rgba(255,255,255,0.05); }
.contact-link-icon.li { background: rgba(10,102,194,0.1); }
.contact-link-icon.em { background: rgba(0,217,255,0.1); }

.contact-link-info { flex: 1; }
.contact-link-label {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  display: block;
  margin-bottom: 0.2rem;
}
.contact-link-value {
  font-size: 0.9rem;
  color: var(--text);
  font-weight: 400;
}

.contact-link-arrow {
  color: var(--text3);
  font-size: 0.9rem;
  transition: all 0.2s;
}
.contact-link:hover .contact-link-arrow {
  color: var(--accent);
  transform: translate(2px, -2px);
}

.contact-right {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 3rem;
}
.contact-form-title {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.5rem;
}
.contact-form-sub {
  font-size: 0.85rem;
  color: var(--text2);
  margin-bottom: 2rem;
  font-weight: 300;
}

.form-row { display: flex; gap: 1rem; }
.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1.25rem;
  flex: 1;
}
.form-label {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text3);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.form-input, .form-textarea {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 2px;
  color: var(--text);
  font-family: var(--font-body);
  font-size: 0.9rem;
  padding: 0.85rem 1rem;
  outline: none;
  transition: border-color 0.2s;
  width: 100%;
}
.form-input:focus, .form-textarea:focus {
  border-color: var(--accent);
  box-shadow: 0 0 0 2px rgba(0,217,255,0.08);
}
.form-input::placeholder, .form-textarea::placeholder { color: var(--text3); }
.form-textarea { resize: vertical; min-height: 120px; }

.form-submit {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: var(--accent);
  color: var(--bg);
  font-family: var(--font-mono);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  border: none;
  padding: 0.9rem 2rem;
  border-radius: 2px;
  cursor: pointer;
  transition: all 0.2s;
  width: 100%;
  justify-content: center;
}
.form-submit:hover {
  background: #00b8d9;
  box-shadow: 0 8px 30px rgba(0,217,255,0.25);
}

/* ── FOOTER ── */
footer {
  border-top: 1px solid var(--border);
  padding: 2rem 3rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.footer-copy {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  color: var(--text3);
  letter-spacing: 0.05em;
}
.footer-copy span { color: var(--accent); }
.footer-heart {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  color: var(--text3);
  letter-spacing: 0.05em;
}
.footer-heart span { color: var(--red); }

/* ── WIDE PROJ LAYOUT ── */
.proj-card.wide .proj-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
}

/* ── ANIMATIONS ── */
.fade-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ── RESPONSIVE ── */
@media (max-width: 900px) {
  nav { padding: 0 1.5rem; }
  .nav-links { display: none; }
  .hero { padding: 0 1.5rem; }
  .hero-stats { display: none; }
  section { padding: 5rem 1.5rem; }
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
  .tech-categories { grid-template-columns: 1fr; }
  .skills-grid { grid-template-columns: 1fr; }
  .projects-grid { grid-template-columns: 1fr; }
  .proj-card.featured, .proj-card.regular, .proj-card.wide, .proj-card.half { grid-column: span 1; }
  .proj-card.wide .proj-content { grid-template-columns: 1fr; }
  .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
  footer { flex-direction: column; gap: 0.5rem; text-align: center; }
  .projects-header { flex-direction: column; }
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">
    <span>// </span>jmcb<span>.dev</span>
  </div>
  <ul class="nav-links">
    <li><a href="#about">Sobre mí</a></li>
    <li><a href="#tech">Tech Stack</a></li>
    <li><a href="#skills">Habilidades</a></li>
    <li><a href="#projects">Proyectos</a></li>
    <li><a href="#experience">Experiencia</a></li>
    <li><a href="#contact">Contacto</a></li>
  </ul>
  <div class="nav-status">
    <div class="status-dot"></div>
    Disponible
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>

  <div class="hero-content fade-in">
    <div class="hero-tag">
      <span>⬡</span>
      Full Stack Software Engineer
    </div>
    <h1 class="hero-name">
      <span class="first">Juan Manuel</span>
      <span class="last">Cruz Beltrán</span>
    </h1>
    <div class="hero-title">// Spring Boot · Angular · Clean Architecture</div>
    <p class="hero-desc">
      Construyo sistemas empresariales robustos aplicando Domain-Driven Design, arquitecturas limpias y prácticas DevOps modernas. Especialista en backends escalables y frontends elegantes.
    </p>
    <div class="hero-ctas">
      <a href="#projects" class="btn-primary">
        ◈ Ver proyectos
      </a>
      <a href="#contact" class="btn-ghost">
        → Contactame
      </a>
      <a href="https://github.com/Mnaue8r32" target="_blank" class="btn-ghost">
        ⌥ GitHub
      </a>
    </div>
  </div>

  <div class="hero-stats">
    <div class="stat-item">
      <div class="stat-value">10<span>+</span></div>
      <div class="stat-label">Proyectos</div>
    </div>
    <div class="stat-item">
      <div class="stat-value">6</div>
      <div class="stat-label">Lenguajes</div>
    </div>
    <div class="stat-item">
      <div class="stat-value">4<span>+</span></div>
      <div class="stat-label">Frameworks</div>
    </div>
    <div class="stat-item">
      <div class="stat-value">3</div>
      <div class="stat-label">Años exp.</div>
    </div>
  </div>

  <div class="hero-scroll">
    <div class="scroll-line"></div>
    Scroll
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-inner">
    <div class="section-label">01 — Sobre mí</div>
    <div class="about-grid">
      <div class="about-text fade-in">
        <h2 class="section-title">
          Construyendo software<br>
          <span class="accent">con propósito</span>
        </h2>
        <br>
        <p>
          Soy <strong>Juan Manuel Cruz Beltrán</strong>, desarrollador Full-Stack especializado en arquitecturas empresariales. Me apasiona crear soluciones que van más allá del código: sistemas mantenibles, escalables y diseñados para durar.
        </p>
        <p>
          Trabajo bajo principios de <strong>Domain-Driven Design</strong>, <strong>Arquitectura Hexagonal</strong> y <strong>Clean Code</strong>, asegurando que la lógica de negocio permanezca independiente de la infraestructura. Cada decisión técnica tiene su porqué.
        </p>
        <p>
          Mis stacks principales son <strong>Java + Spring Boot</strong> en backend y <strong>Angular / React / Vue.js</strong> en frontend, con experiencia sólida en <strong>Docker</strong>, <strong>CI/CD</strong>, y observabilidad con <strong>Prometheus + Grafana</strong>.
        </p>
      </div>
      <div class="about-right fade-in">
        <div class="code-block">
          <div class="code-header">
            <div class="code-dot red"></div>
            <div class="code-dot orange"></div>
            <div class="code-dot green"></div>
            <div class="code-filename">Engineer.java</div>
          </div>
          <div class="code-body">
<span class="code-kw">public class</span> <span class="code-key">JuanManuel</span> <span class="code-kw">implements</span> SeniorEngineer {<br>
&nbsp;<br>
&nbsp;&nbsp;<span class="code-kw">private final</span> List&lt;String&gt; stacks = List.of(<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="code-str">"Spring Boot"</span>, <span class="code-str">"Angular"</span>, <span class="code-str">"FastAPI"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="code-str">"React"</span>, <span class="code-str">"Vue.js"</span>, <span class="code-str">"Docker"</span><br>
&nbsp;&nbsp;);<br>
&nbsp;<br>
&nbsp;&nbsp;<span class="code-kw">private final</span> Architecture pattern =<br>
&nbsp;&nbsp;&nbsp;&nbsp;Architecture.<span class="code-key">DDD_LAYERED</span>;<br>
&nbsp;<br>
&nbsp;&nbsp;<span class="code-cmt">// Siempre disponible para nuevas oportunidades</span><br>
&nbsp;&nbsp;<span class="code-kw">public boolean</span> isAvailable() {<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="code-kw">return</span> <span class="code-num">true</span>;<br>
&nbsp;&nbsp;}<br>
}
          </div>
        </div>
        <div class="about-stats-grid">
          <div class="stat-block">
            <div class="val">10+</div>
            <div class="lbl">Proyectos</div>
          </div>
          <div class="stat-block">
            <div class="val">6</div>
            <div class="lbl">Lenguajes</div>
          </div>
          <div class="stat-block">
            <div class="val">∞</div>
            <div class="lbl">Café</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TECH STACK -->
<section id="tech">
  <div class="section-inner">
    <div class="section-label">02 — Stack Tecnológico</div>
    <h2 class="section-title fade-in">
      Herramientas que<br>
      <span class="accent">domino</span>
    </h2>
    <div class="tech-categories fade-in">

      <div class="tech-cat">
        <div class="tech-cat-header">
          <div class="tech-cat-icon be">⚙</div>
          <div class="tech-cat-title">Backend</div>
        </div>
        <div class="tech-pills">
          <span class="tech-pill be">Spring Boot</span>
          <span class="tech-pill be">FastAPI</span>
          <span class="tech-pill be">.NET / C#</span>
          <span class="tech-pill be">Laravel</span>
          <span class="tech-pill be">Node.js</span>
          <span class="tech-pill be">Java</span>
          <span class="tech-pill be">Python</span>
          <span class="tech-pill be">REST API</span>
          <span class="tech-pill be">OpenAPI</span>
        </div>
      </div>

      <div class="tech-cat">
        <div class="tech-cat-header">
          <div class="tech-cat-icon fe">◧</div>
          <div class="tech-cat-title">Frontend</div>
        </div>
        <div class="tech-pills">
          <span class="tech-pill fe">Angular 18</span>
          <span class="tech-pill fe">React</span>
          <span class="tech-pill fe">Vue.js</span>
          <span class="tech-pill fe">TypeScript</span>
          <span class="tech-pill fe">TailwindCSS</span>
          <span class="tech-pill fe">HTML5</span>
          <span class="tech-pill fe">CSS3</span>
          <span class="tech-pill fe">Bootstrap</span>
          <span class="tech-pill fe">Vite</span>
        </div>
      </div>

      <div class="tech-cat">
        <div class="tech-cat-header">
          <div class="tech-cat-icon mo">◱</div>
          <div class="tech-cat-title">Mobile & Cloud</div>
        </div>
        <div class="tech-pills">
          <span class="tech-pill mo">React Native</span>
          <span class="tech-pill mo">Expo</span>
          <span class="tech-pill mo">AWS S3</span>
          <span class="tech-pill mo">Firebase</span>
          <span class="tech-pill mo">Cloudinary</span>
          <span class="tech-pill mo">Nginx</span>
          <span class="tech-pill mo">Redis</span>
        </div>
      </div>

      <div class="tech-cat">
        <div class="tech-cat-header">
          <div class="tech-cat-icon db">⬡</div>
          <div class="tech-cat-title">DevOps & Bases de Datos</div>
        </div>
        <div class="tech-pills">
          <span class="tech-pill db">Docker</span>
          <span class="tech-pill db">GitHub Actions</span>
          <span class="tech-pill db">SonarCloud</span>
          <span class="tech-pill db">Prometheus</span>
          <span class="tech-pill db">Grafana</span>
          <span class="tech-pill db">PostgreSQL</span>
          <span class="tech-pill db">MySQL</span>
          <span class="tech-pill db">SQL Server</span>
          <span class="tech-pill db">MongoDB</span>
          <span class="tech-pill db">Alembic</span>
          <span class="tech-pill db">Git</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-inner">
    <div class="section-label">03 — Habilidades Clave</div>
    <h2 class="section-title fade-in">
      Más allá del<br>
      <span class="accent">código</span>
    </h2>
    <div class="skills-grid fade-in">

      <div class="skill-card arch">
        <div class="skill-card-icon">🏗</div>
        <div class="skill-card-title">Arquitectura & Diseño</div>
        <ul class="skill-list">
          <li>Clean Architecture / Layered</li>
          <li>Domain-Driven Design (DDD)</li>
          <li>Arquitectura Hexagonal</li>
          <li>Patrones de Diseño</li>
          <li>Sistemas Escalables</li>
          <li>Bounded Contexts</li>
        </ul>
      </div>

      <div class="skill-card eng">
        <div class="skill-card-icon">⚡</div>
        <div class="skill-card-title">Ingeniería & Prácticas</div>
        <ul class="skill-list">
          <li>Metodologías Ágiles (Scrum)</li>
          <li>Revisión de Código</li>
          <li>Principios SOLID</li>
          <li>Optimización de Rendimiento</li>
          <li>CI/CD Pipelines</li>
          <li>Conventional Commits</li>
        </ul>
      </div>

      <div class="skill-card soft">
        <div class="skill-card-icon">🤝</div>
        <div class="skill-card-title">Habilidades Blandas</div>
        <ul class="skill-list">
          <li>Aprendizaje Rápido</li>
          <li>Trabajo en Equipo</li>
          <li>Resolución de Problemas</li>
          <li>Comunicación Efectiva</li>
          <li>Adaptabilidad</li>
          <li>Español (Nativo) · Inglés (B2)</li>
        </ul>
      </div>

    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-inner">
    <div class="section-label">04 — Proyectos Destacados</div>
    <div class="projects-header fade-in">
      <h2 class="section-title">
        Lo que he<br>
        <span class="accent">construido</span>
      </h2>
      <p class="projects-subtitle">
        Desde ERPs empresariales hasta plataformas SaaS y ecosistemas móviles. Cada proyecto con arquitectura limpia y CI/CD integrado.
      </p>
    </div>

    <div class="projects-grid">

      <!-- ERP JMS - Featured -->
      <div class="proj-card featured fade-in">
        <div class="proj-card-top">
          <span class="proj-type-badge badge-fs">Full-Stack Enterprise</span>
          <a href="https://github.com/Mnaue8r32/erp-jms-frontend" target="_blank" class="proj-arrow">↗</a>
        </div>
        <div class="proj-title">ERP JMS — Sistema Completo</div>
        <p class="proj-desc">
          Plataforma ERP completa con frontend Angular 18 y backend Spring Boot. API REST versionada (v1/v2), autenticación JWT, caché Redis, autorización RBAC y seguridad por API Key para integraciones externas.
        </p>
        <ul class="proj-highlights">
          <li>API REST versionada con control de compatibilidad por versión</li>
          <li>Seguridad enterprise: JWT + RBAC + API Key por cliente</li>
          <li>Redis para caché de consultas y sesiones de autenticación</li>
          <li>Docker + CI/CD con GitHub Actions + SonarCloud</li>
        </ul>
        <div class="proj-techs">
          <span class="proj-tech">Spring Boot</span>
          <span class="proj-tech">Angular 18</span>
          <span class="proj-tech">JWT</span>
          <span class="proj-tech">Redis</span>
          <span class="proj-tech">RBAC</span>
          <span class="proj-tech">Docker</span>
          <span class="proj-tech">GitHub Actions</span>
          <span class="proj-tech">SonarCloud</span>
        </div>
      </div>

      <!-- OrdenaYa -->
      <div class="proj-card regular fade-in">
        <div class="proj-card-top">
          <span class="proj-type-badge badge-fs">Full-Stack + Mobile</span>
          <a href="https://github.com/Mnaue8r32/ordenaya-web" target="_blank" class="proj-arrow">↗</a>
        </div>
        <div class="proj-title">OrdenaYa — Ecosistema Completo</div>
        <p class="proj-desc">
          Sistema de pedidos para restaurantes: panel web en React, app móvil en React Native y chatbot inteligente con OpenAI. Tres repositorios, un producto cohesivo.
        </p>
        <ul class="proj-highlights">
          <li>Panel admin con gestión de menú en tiempo real</li>
          <li>App móvil con chatbot OrderBot integrado (OpenAI)</li>
          <li>CI/CD + análisis de calidad con SonarCloud</li>
        </ul>
        <div class="proj-techs">
          <span class="proj-tech">React</span>
          <span class="proj-tech">React Native</span>
          <span class="proj-tech">Node.js</span>
          <span class="proj-tech">Firebase</span>
          <span class="proj-tech">OpenAI</span>
          <span class="proj-tech">Expo</span>
        </div>
      </div>

      <!-- ZyBus -->
      <div class="proj-card half fade-in">
        <div class="proj-card-top">
          <span class="proj-type-badge badge-be">Backend · DDD</span>
          <a href="https://github.com/Mnaue8r32/backend_zybus" target="_blank" class="proj-arrow">↗</a>
        </div>
        <div class="proj-title">ZyBus Backend</div>
        <p class="proj-desc">
          API REST con arquitectura DDD profesional en Python. Módulos desacoplados, Value Objects, use cases, excepciones de dominio y migraciones con Alembic.
        </p>
        <ul class="proj-highlights">
          <li>Arquitectura DDD profesional en Python/FastAPI</li>
          <li>Soft delete, roles y permisos granulares</li>
          <li>Docker + CI/CD integrado</li>
        </ul>
        <div class="proj-techs">
          <span class="proj-tech">Python</span>
          <span class="proj-tech">FastAPI</span>
          <span class="proj-tech">SQLAlchemy</span>
          <span class="proj-tech">Alembic</span>
          <span class="proj-tech">Docker</span>
          <span class="proj-tech">DDD</span>
        </div>
      </div>

      <!-- Facturación -->
      <div class="proj-card half fade-in">
        <div class="proj-card-top">
          <span class="proj-type-badge badge-be">Backend · Java</span>
          <a href="https://github.com/Mnaue8r32/electronic-invoicing-api" target="_blank" class="proj-arrow">↗</a>
        </div>
        <div class="proj-title">Facturación Electrónica CR</div>
        <p class="proj-desc">
          Sistema integrado con la API de Hacienda de Costa Rica. Genera XML firmados digitalmente, envía facturas al sandbox y genera PDFs profesionales con logo SVG.
        </p>
        <ul class="proj-highlights">
          <li>Integración con API gubernamental oficial</li>
          <li>Firma digital de documentos XML</li>
          <li>Conventional Commits + SonarCloud</li>
        </ul>
        <div class="proj-techs">
          <span class="proj-tech">Java</span>
          <span class="proj-tech">Spring Boot</span>
          <span class="proj-tech">XML</span>
          <span class="proj-tech">PDF</span>
          <span class="proj-tech">Maven</span>
        </div>
      </div>

      <!-- Virtual Tour -->
      <div class="proj-card wide fade-in">
        <div class="proj-card-top">
          <span class="proj-type-badge badge-fe">Frontend Creativo</span>
          <a href="https://github.com/Mnaue8r32/virtual-tour-360" target="_blank" class="proj-arrow">↗</a>
        </div>
        <div class="proj-content">
          <div>
            <div class="proj-title">Virtual Tour 360°</div>
            <p class="proj-desc">
              Tour virtual interactivo 360° con soporte para giroscopio del dispositivo y navegación por escenas. Experiencia inmersiva creada con HTML, CSS y JavaScript puro sin dependencias externas.
            </p>
          </div>
          <div>
            <ul class="proj-highlights">
              <li>Soporte nativo para giroscopio via DeviceMotion API</li>
              <li>Navegación inmersiva multi-escena sin frameworks</li>
              <li>CI/CD con GitHub Actions + análisis SonarCloud</li>
            </ul>
            <div class="proj-techs">
              <span class="proj-tech">HTML5</span>
              <span class="proj-tech">CSS3</span>
              <span class="proj-tech">JavaScript</span>
              <span class="proj-tech">DeviceMotion API</span>
              <span class="proj-tech">GitHub Actions</span>
              <span class="proj-tech">SonarCloud</span>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-inner">
    <div class="section-label">05 — Trayectoria</div>
    <h2 class="section-title fade-in">
      Mi <span class="accent">experiencia</span>
    </h2>
    <div class="exp-timeline">

      <div class="exp-item fade-in">
        <div class="exp-dot"></div>
        <div class="exp-meta">
          <span class="exp-period">2026 — Presente</span>
        </div>
        <div class="exp-title-text">Desarrollador Full Stack Senior</div>
        <p class="exp-desc">
          Desarrollo de sistemas empresariales y plataformas escalables aplicando DDD, arquitectura limpia y diseño de APIs. Participación en sistemas ERP, SaaS de facturación electrónica y plataformas de transporte con integración de servicios cloud y procesamiento en tiempo real.
        </p>
        <div class="exp-techs">
          <span class="exp-tech">Spring Boot</span>
          <span class="exp-tech">FastAPI</span>
          <span class="exp-tech">.NET</span>
          <span class="exp-tech">Angular</span>
          <span class="exp-tech">React</span>
          <span class="exp-tech">React Native</span>
          <span class="exp-tech">Docker</span>
          <span class="exp-tech">AWS S3</span>
          <span class="exp-tech">OpenAPI</span>
          <span class="exp-tech">GitHub Actions</span>
          <span class="exp-tech">SonarCloud</span>
        </div>
      </div>

      <div class="exp-item fade-in">
        <div class="exp-dot"></div>
        <div class="exp-meta">
          <span class="exp-period">2025 — 2026</span>
        </div>
        <div class="exp-title-text">Desarrollador Full Stack</div>
        <p class="exp-desc">
          Diseño e implementación de aplicaciones web completas utilizando arquitecturas en capas, Arquitectura Hexagonal y principios SOLID. Desarrollo de APIs REST seguras con JWT y RBAC, despliegue continuo mediante pipelines CI/CD.
        </p>
        <div class="exp-techs">
          <span class="exp-tech">Spring Boot</span>
          <span class="exp-tech">FastAPI</span>
          <span class="exp-tech">Laravel</span>
          <span class="exp-tech">Angular</span>
          <span class="exp-tech">Vue.js</span>
          <span class="exp-tech">Docker</span>
          <span class="exp-tech">JWT</span>
          <span class="exp-tech">RBAC</span>
          <span class="exp-tech">PostgreSQL</span>
          <span class="exp-tech">MongoDB</span>
        </div>
      </div>

      <div class="exp-item fade-in">
        <div class="exp-dot"></div>
        <div class="exp-meta">
          <span class="exp-period">2024 — 2025</span>
        </div>
        <div class="exp-title-text">Desarrollo Web & Escritorio</div>
        <p class="exp-desc">
          Construcción de aplicaciones web y de escritorio integrando APIs externas. Sistemas interactivos aplicando estructuras de datos, concurrencia y patrones de diseño como MVC.
        </p>
        <div class="exp-techs">
          <span class="exp-tech">Java</span>
          <span class="exp-tech">PHP</span>
          <span class="exp-tech">JavaScript</span>
          <span class="exp-tech">Bootstrap</span>
          <span class="exp-tech">Swing</span>
          <span class="exp-tech">OpenWeather API</span>
          <span class="exp-tech">Google Maps API</span>
          <span class="exp-tech">MVC</span>
        </div>
      </div>

      <div class="exp-item fade-in">
        <div class="exp-dot"></div>
        <div class="exp-meta">
          <span class="exp-period">2023 — 2024</span>
        </div>
        <div class="exp-title-text">Formación en Ingeniería de Software</div>
        <p class="exp-desc">
          Fundamentos de programación y desarrollo de lógica computacional. Implementación de aplicaciones como sistemas bancarios y proyectos interactivos aplicando POO y estructuras de datos.
        </p>
        <div class="exp-techs">
          <span class="exp-tech">Java</span>
          <span class="exp-tech">POO</span>
          <span class="exp-tech">Estructuras de Datos</span>
          <span class="exp-tech">Lógica de Programación</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-inner">
    <div class="section-label">06 — Contacto</div>
    <h2 class="section-title fade-in">
      Trabajamos<br>
      <span class="accent">juntos</span>
    </h2>
    <div class="contact-grid fade-in">
      <div class="contact-left">
        <p>
          Estoy disponible para proyectos freelance, posiciones full-time o colaboraciones interesantes. Si buscas un engineer que combine sólida arquitectura técnica con atención al detalle, hablemos.
        </p>
        <div class="contact-links">
          <a href="https://github.com/Mnaue8r32" target="_blank" class="contact-link">
            <div class="contact-link-icon gh">⌥</div>
            <div class="contact-link-info">
              <span class="contact-link-label">GitHub</span>
              <span class="contact-link-value">github.com/Mnaue8r32</span>
            </div>
            <span class="contact-link-arrow">↗</span>
          </a>
          <a href="https://linkedin.com/in/YOUR_LINKEDIN_PROFILE" target="_blank" class="contact-link">
            <div class="contact-link-icon li">in</div>
            <div class="contact-link-info">
              <span class="contact-link-label">LinkedIn</span>
              <span class="contact-link-value">linkedin.com/in/juanmanuelcb</span>
            </div>
            <span class="contact-link-arrow">↗</span>
          </a>
          <a href="mailto:YOUR_EMAIL@example.com" class="contact-link">
            <div class="contact-link-icon em">@</div>
            <div class="contact-link-info">
              <span class="contact-link-label">Email</span>
              <span class="contact-link-value">YOUR_EMAIL@example.com</span>
            </div>
            <span class="contact-link-arrow">↗</span>
          </a>
        </div>
      </div>
      <div class="contact-right">
        <div class="contact-form-title">Envíame un mensaje</div>
        <div class="contact-form-sub">Respondo en menos de 24 horas.</div>
        <div class="form-row">
          <div class="form-group">
            <label class="form-label">Nombre</label>
            <input type="text" class="form-input" placeholder="Tu nombre" />
          </div>
          <div class="form-group">
            <label class="form-label">Email</label>
            <input type="email" class="form-input" placeholder="tu@email.com" />
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Asunto</label>
          <input type="text" class="form-input" placeholder="¿De qué trata?" />
        </div>
        <div class="form-group">
          <label class="form-label">Mensaje</label>
          <textarea class="form-textarea" placeholder="Cuéntame sobre tu proyecto..."></textarea>
        </div>
        <button class="form-submit">→ Enviar mensaje</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-copy">
    © 2026 <span>Juan Manuel Cruz Beltrán</span> — Full Stack Engineer
  </div>
  <div class="footer-heart">
    Diseñado y desarrollado con <span>♥</span> y demasiado café
  </div>
</footer>

<script>
// Intersection Observer for fade-in animations
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry, i) => {
    if (entry.isIntersecting) {
      setTimeout(() => {
        entry.target.classList.add('visible');
      }, i * 80);
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

// Smooth active nav highlighting
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');

window.addEventListener('scroll', () => {
  let current = '';
  sections.forEach(section => {
    const sectionTop = section.offsetTop - 100;
    if (scrollY >= sectionTop) current = section.getAttribute('id');
  });
  navLinks.forEach(link => {
    link.style.color = link.getAttribute('href') === `#${current}` 
      ? 'var(--accent)' 
      : '';
  });
});

// Hero fade in on load
document.querySelector('.hero-content').style.opacity = '0';
document.querySelector('.hero-content').style.transform = 'translateY(30px)';
setTimeout(() => {
  document.querySelector('.hero-content').style.transition = 'all 0.8s ease';
  document.querySelector('.hero-content').style.opacity = '1';
  document.querySelector('.hero-content').style.transform = 'translateY(0)';
}, 100);
</script>
</body>
</html>
