<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jeeva N — Embedded & Automotive Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Inter:wght@300;400;500;600&family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;scrollbar-width:thin;scrollbar-color:#00f5c4 #0a0a12}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:#0a0a12}
::-webkit-scrollbar-thumb{background:#00f5c4;border-radius:2px}

:root{
  --bg:#060710;
  --bg2:#0d0f1f;
  --bg3:#111428;
  --surface:rgba(255,255,255,0.04);
  --surface2:rgba(255,255,255,0.07);
  --cyan:#00f5c4;
  --cyan2:#00c9ff;
  --violet:#7c3aed;
  --violet2:#a855f7;
  --orange:#ff6b35;
  --text:#e8eaf0;
  --muted:#6b7280;
  --muted2:#9ca3af;
  --border:rgba(255,255,255,0.08);
  --glow-cyan:0 0 20px rgba(0,245,196,0.3),0 0 60px rgba(0,245,196,0.1);
  --glow-violet:0 0 20px rgba(168,85,247,0.3),0 0 60px rgba(168,85,247,0.1);
  --font-display:'Orbitron',monospace;
  --font-body:'Inter',sans-serif;
  --font-mono:'JetBrains Mono',monospace;
}

body{
  background:var(--bg);color:var(--text);
  font-family:var(--font-body);font-size:16px;line-height:1.7;
  overflow-x:hidden;
}

/* ─── CANVAS BACKGROUND ─── */
#bg-canvas{
  position:fixed;top:0;left:0;width:100%;height:100%;
  z-index:0;pointer-events:none;opacity:0.5;
}

/* ─── NAV ─── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:1000;
  display:flex;justify-content:space-between;align-items:center;
  padding:0 4rem;height:60px;
  background:rgba(6,7,16,0.85);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
}
.nav-logo{
  font-family:var(--font-display);font-size:13px;letter-spacing:0.15em;
  color:var(--cyan);
  text-shadow:var(--glow-cyan);
}
.nav-links{display:flex;gap:0;list-style:none}
.nav-links a{
  font-family:var(--font-mono);font-size:11px;letter-spacing:0.1em;
  text-transform:uppercase;text-decoration:none;
  color:var(--muted);padding:0 1.2rem;line-height:60px;display:block;
  position:relative;transition:color 0.2s;
}
.nav-links a::after{
  content:'';position:absolute;bottom:0;left:1.2rem;right:1.2rem;
  height:2px;background:var(--cyan);
  transform:scaleX(0);transition:transform 0.3s;
}
.nav-links a:hover{color:var(--text)}
.nav-links a:hover::after{transform:scaleX(1)}
.nav-cta{
  font-family:var(--font-mono);font-size:11px;letter-spacing:0.1em;
  text-transform:uppercase;text-decoration:none;
  padding:.4rem 1.2rem;
  border:1px solid var(--cyan);color:var(--cyan);
  transition:all 0.2s;
  box-shadow:0 0 10px rgba(0,245,196,0.2);
}
.nav-cta:hover{background:var(--cyan);color:var(--bg);box-shadow:var(--glow-cyan)}

/* ─── CURSOR GLOW ─── */
.cursor-glow{
  position:fixed;width:400px;height:400px;
  border-radius:50%;
  background:radial-gradient(circle,rgba(0,245,196,0.06) 0%,transparent 70%);
  pointer-events:none;z-index:1;
  transform:translate(-50%,-50%);
  transition:transform 0.1s linear;
}

/* ─── HERO ─── */
.hero{
  min-height:100vh;
  display:flex;flex-direction:column;justify-content:center;
  padding:60px 4rem 0;
  position:relative;z-index:2;
  overflow:hidden;
}
.hero-bg-text{
  position:absolute;
  font-family:var(--font-display);
  font-size:clamp(10rem,20vw,22rem);
  font-weight:900;
  color:rgba(0,245,196,0.025);
  line-height:1;
  top:50%;left:50%;
  transform:translate(-50%,-50%);
  white-space:nowrap;
  pointer-events:none;
  letter-spacing:-0.05em;
  user-select:none;
}
.hero-content{position:relative;z-index:2;max-width:900px}

.hero-badge{
  display:inline-flex;align-items:center;gap:10px;
  font-family:var(--font-mono);font-size:11px;letter-spacing:0.15em;
  text-transform:uppercase;color:var(--cyan);
  margin-bottom:2rem;
  opacity:0;animation:fadeSlideUp 0.8s 0.2s forwards;
}
.hero-badge-dot{
  width:8px;height:8px;border-radius:50%;background:var(--cyan);
  box-shadow:0 0 8px var(--cyan);
  animation:blink 1.5s infinite;
}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0.2}}

.hero-name{
  font-family:var(--font-display);
  font-size:clamp(3.5rem,9vw,8rem);
  font-weight:800;
  line-height:0.9;
  letter-spacing:-0.02em;
  margin-bottom:1.5rem;
  opacity:0;animation:fadeSlideUp 0.8s 0.4s forwards;
}
.hero-name .line1{display:block;color:var(--text)}
.hero-name .line2{
  display:block;
  background:linear-gradient(90deg,var(--cyan),var(--cyan2),var(--violet2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
  animation:gradientShift 4s ease infinite;
  background-size:200% auto;
}
@keyframes gradientShift{0%{background-position:0% center}50%{background-position:100% center}100%{background-position:0% center}}

.hero-title{
  font-family:var(--font-mono);font-size:14px;letter-spacing:0.05em;
  color:var(--muted2);margin-bottom:2rem;
  opacity:0;animation:fadeSlideUp 0.8s 0.6s forwards;
}
.hero-title .bracket{color:var(--cyan);opacity:0.6}
.hero-title .role{color:var(--violet2)}

.hero-desc{
  font-size:17px;color:var(--muted2);line-height:1.9;
  max-width:580px;margin-bottom:3rem;
  opacity:0;animation:fadeSlideUp 0.8s 0.8s forwards;
  border-left:2px solid var(--cyan);padding-left:1.2rem;
}

.hero-actions{
  display:flex;gap:1rem;align-items:center;flex-wrap:wrap;
  opacity:0;animation:fadeSlideUp 0.8s 1s forwards;
}
.btn-primary{
  font-family:var(--font-mono);font-size:12px;font-weight:500;
  letter-spacing:0.1em;text-transform:uppercase;text-decoration:none;
  padding:.85rem 2.5rem;
  background:linear-gradient(135deg,var(--cyan),var(--cyan2));
  color:var(--bg);border:none;cursor:pointer;
  position:relative;overflow:hidden;
  transition:transform 0.2s,box-shadow 0.2s;
  clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0% 100%);
}
.btn-primary::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(255,255,255,0.2),transparent);
  opacity:0;transition:opacity 0.2s;
}
.btn-primary:hover{transform:translateY(-2px);box-shadow:var(--glow-cyan)}
.btn-primary:hover::before{opacity:1}

.btn-secondary{
  font-family:var(--font-mono);font-size:12px;font-weight:500;
  letter-spacing:0.1em;text-transform:uppercase;text-decoration:none;
  padding:.85rem 2.5rem;
  background:transparent;
  color:var(--text);
  border:1px solid rgba(255,255,255,0.15);
  cursor:pointer;transition:all 0.2s;
  clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0% 100%);
}
.btn-secondary:hover{
  border-color:var(--violet2);color:var(--violet2);
  box-shadow:0 0 20px rgba(168,85,247,0.2);
}

.hero-stats{
  position:absolute;right:4rem;top:50%;transform:translateY(-50%);
  display:flex;flex-direction:column;gap:0;
  opacity:0;animation:fadeSlideRight 0.8s 1.2s forwards;
  z-index:2;
}
.stat-item{
  padding:1.5rem;
  border:1px solid var(--border);
  background:var(--surface);
  backdrop-filter:blur(10px);
  border-bottom:none;
  min-width:140px;
  position:relative;overflow:hidden;
  transition:background 0.2s,border-color 0.2s;
}
.stat-item:last-child{border-bottom:1px solid var(--border)}
.stat-item::before{
  content:'';position:absolute;top:0;left:0;width:2px;height:100%;
  background:var(--cyan);transform:scaleY(0);transform-origin:bottom;
  transition:transform 0.3s;
}
.stat-item:hover::before{transform:scaleY(1)}
.stat-item:hover{background:var(--surface2);border-color:rgba(0,245,196,0.2)}
.stat-num{
  font-family:var(--font-display);font-size:1.8rem;font-weight:700;
  color:var(--cyan);line-height:1;margin-bottom:.3rem;
  text-shadow:var(--glow-cyan);
}
.stat-label{font-family:var(--font-mono);font-size:10px;letter-spacing:0.1em;color:var(--muted);text-transform:uppercase}

.scroll-indicator{
  position:absolute;right:4rem;left:auto;bottom:2rem;
  display:flex;align-items:center;gap:12px;
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.15em;
  color:var(--muted);text-transform:uppercase;
  opacity:0;animation:fadeIn 1s 1.5s forwards;
  z-index:2;
}
.scroll-line{
  width:60px;height:1px;background:linear-gradient(90deg,var(--cyan),transparent);
  position:relative;overflow:hidden;
}
.scroll-line::after{
  content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;
  background:var(--cyan);animation:scanLine 2s 1.5s infinite;
}
@keyframes scanLine{0%{left:-100%}100%{left:200%}}

@keyframes fadeSlideUp{from{opacity:0;transform:translateY(30px)}to{opacity:1;transform:none}}
@keyframes fadeSlideRight{from{opacity:0;transform:translate(30px,-50%)}to{opacity:1;transform:translate(0,-50%)}}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}

/* ─── SECTION BASE ─── */
section{position:relative;z-index:2}
.section-wrap{padding:7rem 4rem;max-width:1300px;margin:0 auto}

.section-eyebrow{
  display:flex;align-items:center;gap:1rem;
  font-family:var(--font-mono);font-size:11px;letter-spacing:0.2em;
  color:var(--cyan);text-transform:uppercase;
  margin-bottom:1.5rem;
}
.eyebrow-line{width:30px;height:1px;background:var(--cyan);box-shadow:0 0 6px var(--cyan)}

.section-heading{
  font-family:var(--font-display);
  font-size:clamp(2rem,4vw,3.2rem);
  font-weight:700;letter-spacing:-0.01em;
  line-height:1.1;margin-bottom:4rem;
}
.section-heading .accent{color:var(--cyan)}
.section-heading .accent-v{color:var(--violet2)}

/* ─── DIVIDERS ─── */
.section-divider{
  height:1px;
  background:linear-gradient(90deg,transparent,var(--border) 20%,var(--border) 80%,transparent);
}

/* ─── ABOUT ─── */
#about{background:linear-gradient(180deg,var(--bg) 0%,var(--bg2) 100%)}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:start}
.about-text p{font-size:16px;color:var(--muted2);line-height:1.9;margin-bottom:1.2rem}
.about-text p strong{color:var(--text);font-weight:600}
.about-text p:last-child{margin-bottom:}
.about-tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:2rem}
.about-tag{
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.08em;
  padding:5px 14px;text-transform:uppercase;
  background:rgba(0,245,196,0.08);
  border:1px solid rgba(0,245,196,0.2);
  color:var(--cyan);
  transition:all 0.2s;
}
.about-tag:hover{background:rgba(0,245,196,0.15);box-shadow:0 0 12px rgba(0,245,196,0.2)}
.about-tag.v{
  background:rgba(168,85,247,0.08);
  border-color:rgba(168,85,247,0.2);
  color:var(--violet2);
}
.about-tag.v:hover{background:rgba(168,85,247,0.15);box-shadow:0 0 12px rgba(168,85,247,0.2)}

.about-card{
  background:var(--surface);
  border:1px solid var(--border);
  backdrop-filter:blur(10px);
  padding:2.5rem;
  position:relative;overflow:hidden;
}
.about-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--cyan),var(--violet2));
}
.about-card-title{
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.15em;
  text-transform:uppercase;color:var(--cyan);margin-bottom:1.5rem;
}
.info-row{
  display:flex;justify-content:space-between;align-items:flex-start;
  padding:.85rem 0;border-bottom:1px solid var(--border);
  gap:1rem;
}
.info-row:last-child{border-bottom:none;padding-bottom:0}
.info-key{font-family:var(--font-mono);font-size:11px;color:var(--muted);letter-spacing:0.05em}
.info-val{font-size:13px;color:var(--text);font-weight:500;text-align:right}
.info-val.cyan{color:var(--cyan)}
.info-val.green{color:#4ade80}

/* ─── EXPERIENCE ─── */
#experience{background:var(--bg2)}
.exp-timeline{
  display:flex;flex-direction:column;gap:2px;
  position:relative;
}
.exp-timeline::before{
  content:'';
  position:absolute;left:calc(2.5rem - 1px);top:0;bottom:0;width:1px;
  background:linear-gradient(180deg,var(--cyan),var(--violet2),transparent);
}
.exp-item{
  display:grid;grid-template-columns:5rem 1fr;gap:0;
  position:relative;
  opacity:0;transform:translateX(-20px);
  transition:opacity 0.5s,transform 0.5s;
}
.exp-item.vis{opacity:1;transform:none}
.exp-dot-col{
  display:flex;flex-direction:column;align-items:center;
  padding-top:.35rem;
}
.exp-dot{
  width:12px;height:12px;border-radius:50%;
  background:var(--cyan);border:2px solid var(--bg2);
  box-shadow:0 0 12px var(--cyan);
  flex-shrink:0;position:relative;z-index:1;
}
.exp-dot.violet{background:var(--violet2);box-shadow:0 0 12px var(--violet2)}
.exp-dot.orange{background:var(--orange);box-shadow:0 0 12px var(--orange)}
.exp-body{
  background:var(--surface);
  border:1px solid var(--border);
  padding:2rem 2.5rem;margin-bottom:2px;
  position:relative;overflow:hidden;
  transition:border-color 0.3s,background 0.3s;
}
.exp-body:hover{border-color:rgba(0,245,196,0.25);background:var(--surface2)}
.exp-body::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:3px;
  background:linear-gradient(180deg,var(--cyan),var(--cyan2));
  transform:scaleY(0);transform-origin:top;transition:transform 0.3s;
}
.exp-item:nth-child(2) .exp-body::before{background:linear-gradient(180deg,var(--violet),var(--violet2))}
.exp-item:nth-child(3) .exp-body::before{background:var(--orange)}
.exp-body:hover::before{transform:scaleY(1)}
.exp-org{
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.15em;
  text-transform:uppercase;color:var(--cyan);margin-bottom:.5rem;
}
.exp-item:nth-child(2) .exp-org{color:var(--violet2)}
.exp-item:nth-child(3) .exp-org{color:var(--orange)}
.exp-role{
  font-family:var(--font-display);font-size:1.15rem;font-weight:600;
  margin-bottom:1.2rem;line-height:1.3;
}
.exp-bullets{list-style:none;display:flex;flex-direction:column;gap:.5rem}
.exp-bullets li{
  font-size:14px;color:var(--muted2);padding-left:1.2rem;
  position:relative;line-height:1.6;
}
.exp-bullets li::before{
  content:'›';position:absolute;left:0;color:var(--cyan);font-size:16px;line-height:1.5;
}
.exp-item:nth-child(2) .exp-bullets li::before{color:var(--violet2)}
.exp-item:nth-child(3) .exp-bullets li::before{color:var(--orange)}

/* ─── PROJECTS ─── */
#projects{background:var(--bg)}
.projects-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:2px;
}
.project-card{
  background:var(--surface);border:1px solid var(--border);
  padding:3rem;position:relative;overflow:hidden;
  transition:transform 0.3s,border-color 0.3s;
  cursor:default;
}
.project-card::after{
  content:'';
  position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(0,245,196,0.05) 0%,transparent 60%);
  opacity:0;transition:opacity 0.3s;
}
.project-card:hover{transform:translateY(-4px);border-color:rgba(0,245,196,0.3)}
.project-card:hover::after{opacity:1}
.project-card:nth-child(2)::after{background:linear-gradient(135deg,rgba(168,85,247,0.05) 0%,transparent 60%)}
.project-card:nth-child(2):hover{border-color:rgba(168,85,247,0.3)}

.project-num{
  font-family:var(--font-display);
  font-size:4rem;font-weight:900;
  color:rgba(255,255,255,0.04);
  position:absolute;top:1.5rem;right:2rem;
  line-height:1;pointer-events:none;
}
.project-icon{
  width:48px;height:48px;
  background:linear-gradient(135deg,rgba(0,245,196,0.15),rgba(0,201,255,0.15));
  border:1px solid rgba(0,245,196,0.3);
  display:flex;align-items:center;justify-content:center;
  margin-bottom:1.5rem;font-size:22px;
  position:relative;z-index:1;
}
.project-card:nth-child(2) .project-icon{
  background:linear-gradient(135deg,rgba(168,85,247,0.15),rgba(124,58,237,0.15));
  border-color:rgba(168,85,247,0.3);
}
.project-title{
  font-family:var(--font-display);font-size:1.15rem;font-weight:600;
  margin-bottom:1rem;line-height:1.3;position:relative;z-index:1;
}
.project-desc{font-size:14px;color:var(--muted2);line-height:1.8;margin-bottom:1.5rem;position:relative;z-index:1}
.project-tags{display:flex;flex-wrap:wrap;gap:6px;position:relative;z-index:1}
.project-tag{
  font-family:var(--font-mono);font-size:9px;letter-spacing:0.08em;
  padding:3px 10px;text-transform:uppercase;
  background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.1);
  color:var(--muted2);transition:all 0.2s;
}
.project-card:hover .project-tag{border-color:rgba(0,245,196,0.2);color:var(--cyan)}
.project-card:nth-child(2):hover .project-tag{border-color:rgba(168,85,247,0.2);color:var(--violet2)}

/* ─── SKILLS ─── */
#skills{background:var(--bg2)}
.skills-layout{display:grid;grid-template-columns:1fr 1fr;gap:3rem}
.skill-group{margin-bottom:2.5rem}
.skill-group-label{
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.18em;
  text-transform:uppercase;color:var(--cyan);margin-bottom:1.2rem;
  display:flex;align-items:center;gap:.5rem;
}
.skill-group-label::before{content:'▹';color:var(--cyan)}
.skill-bar-item{margin-bottom:1rem}
.skill-bar-header{
  display:flex;justify-content:space-between;
  font-size:13px;margin-bottom:.4rem;
}
.skill-name{color:var(--text);font-weight:500}
.skill-pct{font-family:var(--font-mono);font-size:11px;color:var(--cyan)}
.skill-track{
  height:3px;background:rgba(255,255,255,0.06);
  position:relative;overflow:hidden;
}
.skill-fill{
  height:100%;background:linear-gradient(90deg,var(--cyan),var(--cyan2));
  width:0;transition:width 1s cubic-bezier(0.25,0.46,0.45,0.94);
  position:relative;
}
.skill-fill::after{
  content:'';position:absolute;right:0;top:-4px;
  width:2px;height:11px;
  background:var(--cyan);box-shadow:0 0 8px var(--cyan);
}
.skill-fill.v{background:linear-gradient(90deg,var(--violet),var(--violet2))}
.skill-fill.v::after{background:var(--violet2);box-shadow:0 0 8px var(--violet2)}

.tech-grid{
  display:grid;grid-template-columns:repeat(3,1fr);gap:2px;
}
.tech-chip{
  background:var(--surface);
  border:1px solid var(--border);
  padding:.85rem 1rem;
  font-family:var(--font-mono);font-size:11px;
  letter-spacing:0.06em;text-transform:uppercase;
  color:var(--muted2);text-align:center;
  transition:all 0.2s;
  position:relative;overflow:hidden;
}
.tech-chip::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(0,245,196,0.08),transparent);
  opacity:0;transition:opacity 0.2s;
}
.tech-chip:hover{color:var(--cyan);border-color:rgba(0,245,196,0.3)}
.tech-chip:hover::before{opacity:1}

/* ─── CERTS ─── */
#certifications{background:var(--bg)}
.certs-grid{
  display:grid;grid-template-columns:repeat(4,1fr);gap:2px;
}
.cert-card{
  background:var(--surface);border:1px solid var(--border);
  padding:2rem 1.75rem;
  position:relative;overflow:hidden;
  transition:border-color 0.3s,transform 0.3s;
}
.cert-card:hover{border-color:rgba(0,245,196,0.3);transform:translateY(-3px)}
.cert-card::after{
  content:'';
  position:absolute;bottom:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--cyan),var(--violet2));
  transform:scaleX(0);transform-origin:left;
  transition:transform 0.3s;
}
.cert-card:hover::after{transform:scaleX(1)}
.cert-badge-wrap{
  width:44px;height:44px;
  background:rgba(0,245,196,0.1);border:1px solid rgba(0,245,196,0.25);
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font-display);font-size:9px;font-weight:700;
  color:var(--cyan);margin-bottom:1.2rem;letter-spacing:0.05em;
}
.cert-name{font-size:14px;font-weight:600;line-height:1.4;margin-bottom:.4rem;color:var(--text)}
.cert-issuer{font-family:var(--font-mono);font-size:10px;color:var(--muted);letter-spacing:0.05em}

/* ─── CONTACT ─── */
#contact{
  background:linear-gradient(180deg,var(--bg2) 0%,var(--bg) 100%);
  position:relative;overflow:hidden;
}
#contact::before{
  content:'';position:absolute;
  top:50%;left:50%;transform:translate(-50%,-50%);
  width:600px;height:600px;border-radius:50%;
  background:radial-gradient(circle,rgba(0,245,196,0.04) 0%,transparent 70%);
  pointer-events:none;
}
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:start}
.contact-left h2{
  font-family:var(--font-display);
  font-size:clamp(2.2rem,4.5vw,3.5rem);
  font-weight:700;line-height:1.05;
  margin-bottom:1.2rem;letter-spacing:-0.01em;
}
.contact-left h2 .g{
  background:linear-gradient(90deg,var(--cyan),var(--violet2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
}
.contact-left p{font-size:15px;color:var(--muted2);line-height:1.8;margin-bottom:2rem}
.avail{
  display:inline-flex;align-items:center;gap:.6rem;
  font-family:var(--font-mono);font-size:10px;letter-spacing:0.12em;
  text-transform:uppercase;
  padding:.5rem 1rem;
  border:1px solid rgba(74,222,128,0.3);
  background:rgba(74,222,128,0.08);color:#4ade80;
  margin-bottom:2.5rem;
}
.avail-pulse{
  width:8px;height:8px;border-radius:50%;background:#4ade80;
  box-shadow:0 0 8px #4ade80;animation:pulse2 2s infinite;
}
@keyframes pulse2{0%,100%{box-shadow:0 0 8px #4ade80}50%{box-shadow:0 0 16px #4ade80,0 0 24px #4ade80}}

.contact-links{display:flex;flex-direction:column;gap:2px}
.contact-link{
  display:flex;align-items:center;gap:1.2rem;
  padding:1.2rem 1.5rem;
  background:var(--surface);border:1px solid var(--border);
  text-decoration:none;color:var(--text);
  transition:all 0.2s;
  position:relative;overflow:hidden;
}
.contact-link::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:2px;
  background:var(--cyan);transform:scaleY(0);transition:transform 0.2s;
}
.contact-link:hover{background:var(--surface2);border-color:rgba(0,245,196,0.2);transform:translateX(4px)}
.contact-link:hover::before{transform:scaleY(1)}
.link-icon{
  width:36px;height:36px;
  background:rgba(0,245,196,0.1);border:1px solid rgba(0,245,196,0.2);
  display:flex;align-items:center;justify-content:center;
  font-size:16px;flex-shrink:0;
}
.link-meta{}
.link-type{font-family:var(--font-mono);font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-bottom:2px}
.link-val{font-size:14px;font-weight:500}
.link-arrow{margin-left:auto;color:var(--muted);font-size:18px;transition:color 0.2s,transform 0.2s}
.contact-link:hover .link-arrow{color:var(--cyan);transform:translateX(3px)}

/* ─── FOOTER ─── */
footer{
  border-top:1px solid var(--border);
  padding:1.75rem 4rem;
  display:flex;justify-content:space-between;align-items:center;
  position:relative;z-index:2;
  background:var(--bg);
}
footer span{font-family:var(--font-mono);font-size:10px;letter-spacing:0.08em;color:var(--muted);text-transform:uppercase}
.footer-status{display:flex;align-items:center;gap:.5rem;color:#4ade80}
.footer-status::before{
  content:'';width:6px;height:6px;border-radius:50%;
  background:#4ade80;box-shadow:0 0 6px #4ade80;
}

/* ─── SCROLL REVEAL ─── */
.sr{opacity:0;transform:translateY(24px);transition:opacity 0.6s,transform 0.6s}
.sr.vis{opacity:1;transform:none}
.sr-left{opacity:0;transform:translateX(-24px);transition:opacity 0.6s,transform 0.6s}
.sr-left.vis{opacity:1;transform:none}

/* ─── RESPONSIVE ─── */
@media(max-width:900px){
  nav{padding:0 1.25rem}
  .nav-links,.nav-cta{display:none}
  .hero{padding:80px 1.5rem 0}
  .hero-stats{position:static;transform:none;flex-direction:row;flex-wrap:wrap;margin-top:3rem;animation:none;opacity:1}
  .stat-item{flex:1;min-width:120px;border-bottom:1px solid var(--border)!important}
  .scroll-indicator{left:1.5rem}
  .section-wrap{padding:4rem 1.5rem}
  .about-grid,.contact-grid{grid-template-columns:1fr}
  .projects-grid{grid-template-columns:1fr}
  .skills-layout{grid-template-columns:1fr}
  .certs-grid{grid-template-columns:1fr 1fr}
  footer{padding:1.25rem 1.5rem;flex-direction:column;gap:.5rem;text-align:center}
}

/* ─── RESUME DOWNLOAD BUTTON ─── */
.resume-download-btn {
  display: block;
  text-decoration: none;
  margin-top: 2rem;
  border: 1px solid rgba(0,245,196,0.3);
  background: linear-gradient(135deg, rgba(0,245,196,0.06), rgba(0,201,255,0.04));
  position: relative;
  overflow: hidden;
  transition: border-color 0.3s, transform 0.2s;
  clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
}
.resume-download-btn:hover {
  border-color: var(--cyan);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(0,245,196,0.15), 0 0 0 1px rgba(0,245,196,0.2);
}
.resume-btn-inner {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.1rem 1.5rem;
  position: relative;
  z-index: 1;
}
.resume-btn-icon {
  width: 42px; height: 42px;
  background: rgba(0,245,196,0.12);
  border: 1px solid rgba(0,245,196,0.3);
  display: flex; align-items: center; justify-content: center;
  color: var(--cyan);
  flex-shrink: 0;
  transition: background 0.2s;
}
.resume-download-btn:hover .resume-btn-icon {
  background: rgba(0,245,196,0.2);
}
.resume-btn-text {
  flex: 1;
}
.resume-btn-label {
  display: block;
  font-family: var(--font-display);
  font-size: 13px;
  font-weight: 600;
  color: var(--cyan);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
.resume-btn-sub {
  display: block;
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--muted);
  letter-spacing: 0.08em;
  margin-top: 2px;
}
.resume-btn-arrow {
  color: var(--cyan);
  opacity: 0.6;
  transition: opacity 0.2s, transform 0.2s;
}
.resume-download-btn:hover .resume-btn-arrow {
  opacity: 1;
  transform: translateY(2px);
}
.resume-btn-progress {
  position: absolute;
  bottom: 0; left: 0;
  height: 2px;
  width: 0%;
  background: linear-gradient(90deg, var(--cyan), var(--cyan2));
  transition: width 0.4s cubic-bezier(0.25,0.46,0.45,0.94);
}
.resume-download-btn:hover .resume-btn-progress {
  width: 100%;
}
/* scanning line effect */
.resume-download-btn::after {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 60%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0,245,196,0.06), transparent);
  transition: left 0.6s ease;
}
.resume-download-btn:hover::after {
  left: 150%;
}

</style>
</head>
<body>

<!-- ANIMATED BACKGROUND CANVAS -->
<canvas id="bg-canvas"></canvas>
<div class="cursor-glow" id="cursorGlow"></div>

<!-- NAV -->
<nav>
  <span class="nav-logo">JEEVA_N</span>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="mailto:nagarathinamjeeva7@gmail.com" class="nav-cta">Hire Me</a>
</nav>

<!-- HERO -->
<section class="hero" id="top">
  <div class="hero-bg-text">ECE</div>
  <div class="hero-content">
    <div class="hero-badge">
      <span class="hero-badge-dot"></span>
      <span id="typed-badge">Electronics &amp; Communication Engineering</span>
    </div>
    <h1 class="hero-name">
      <span class="line1">Jeeva</span>
      <span class="line2" id="glitch-name">N.</span>
    </h1>
    <p class="hero-title">
      <span class="bracket">[</span>
      <span class="role">Embedded Systems</span>
      <span class="bracket"> / </span>
      <span class="role" style="color:var(--cyan2)">Automotive Validation</span>
      <span class="bracket"> / </span>
      <span class="role" style="color:var(--violet2)">IoT Engineer</span>
      <span class="bracket">]</span>
    </p>
    <p class="hero-desc">
      Building reliable, intelligent hardware-software systems. Hands-on with CAN bus, Python automation, and ESP32 embedded development.
    </p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary">Get In Touch</a>
      <a href="#experience" class="btn-secondary">View Experience →</a>
    </div>
  </div>

  <div class="hero-stats">
    <div class="stat-item">
      <div class="stat-num" data-count="789" data-decimal="true">0</div>
      <div class="stat-label">CGPA Score</div>
    </div>
    <div class="stat-item">
      <div class="stat-num" data-count="3">0</div>
      <div class="stat-label">Internships</div>
    </div>
    <div class="stat-item">
      <div class="stat-num" data-count="4">0</div>
      <div class="stat-label">Certifications</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">2026</div>
      <div class="stat-label">Graduating</div>
    </div>
  </div>

  <div class="scroll-indicator">                                                                                                            
    <div class="scroll-line"></div>
    scroll to explore
  </div>
</section>

<div class="section-divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="section-wrap">
    <div class="section-eyebrow sr"><span class="eyebrow-line"></span> About</div>
    <div class="about-grid">
      <div class="sr">
        <h2 class="section-heading">Hardware meets<br>software at <span class="accent">my desk</span></h2>
        <div class="about-text">
          <p>I'm a <strong>final-year Electronics &amp; Communication Engineering</strong> student at Adhiparasakthi Engineering College, graduating 2026 with a CGPA of 7.89.</p>
          <p>My internships at <strong>Pricol Limited</strong> — a leading automotive instrument cluster manufacturer — gave me production-level exposure to CAN bus systems, Python validation pipelines, and the precision demands of automotive-grade software.</p>
          <p>I also built real IoT systems from scratch and programmed ESP32 microcontrollers at <strong>Retech Solutions</strong>. I'm seeking an entry-level embedded or automotive role where I can ship real hardware-software systems.</p>
        </div>
        <div class="about-tags">
          <span class="about-tag">Automotive Validation</span>
          <span class="about-tag">CAN Bus</span>
          <span class="about-tag">Python Automation</span>
          <span class="about-tag v">ESP32</span>
          <span class="about-tag v">Embedded C</span>
          <span class="about-tag v">IoT Systems</span>
        </div>
      </div>
      <div class="sr" style="transition-delay:0.15s">
        <div class="about-card">
          <div class="about-card-title">// profile.json</div>
          <div class="info-row"><span class="info-key">degree</span><span class="info-val">B.E. ECE</span></div>
          <div class="info-row"><span class="info-key">college</span><span class="info-val">Adhiparasakthi Engg.</span></div>
          <div class="info-row"><span class="info-key">cgpa</span><span class="info-val cyan">7.89 / 10</span></div>
          <div class="info-row"><span class="info-key">graduating</span><span class="info-val cyan">2026</span></div>
          <div class="info-row"><span class="info-key">location</span><span class="info-val">Paramakudi, TN</span></div>
          <div class="info-row"><span class="info-key">focus</span><span class="info-val">Embedded &amp; Automotive</span></div>
          <div class="info-row"><span class="info-key">status</span><span class="info-val green">Available ●</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-wrap">
    <div class="section-eyebrow sr"><span class="eyebrow-line"></span> Experience</div>
    <h2 class="section-heading sr">Where I've <span class="accent">shipped</span> real work</h2>
    <div class="exp-timeline">
      <div class="exp-item">
        <div class="exp-dot-col"><div class="exp-dot"></div></div>
        <div class="exp-body">
          <div class="exp-org">Pricol Limited</div>
          <div class="exp-role">Automotive Digital Cluster Validation Intern</div>
          <ul class="exp-bullets">
            <li>Developed Python automation scripts improving validation efficiency for automotive digital cluster testing.</li>
            <li>Automated CAN message decoding, log parsing, and signal verification to enhance testing accuracy.</li>
            <li>Generated automated validation reports, significantly reducing manual effort through repeatable workflows.</li>
          </ul>
        </div>
      </div>
      <div class="exp-item">
        <div class="exp-dot-col"><div class="exp-dot violet"></div></div>
        <div class="exp-body">
          <div class="exp-org">Pricol Limited</div>
          <div class="exp-role">RFQ Technical Proposal &amp; Hardware Design Intern</div>
          <ul class="exp-bullets">
            <li>Supported RFQ proposal preparation through detailed requirement comparison and technical analysis.</li>
            <li>Assisted with hardware design learning and contributed to product development activities.</li>
          </ul>
        </div>
      </div>
      <div class="exp-item">
        <div class="exp-dot-col"><div class="exp-dot orange"></div></div>
        <div class="exp-body">
          <div class="exp-org">Retech Solutions Pvt. Ltd.</div>
          <div class="exp-role">Embedded Systems Intern</div>
          <ul class="exp-bullets">
            <li>Built an ESP32-based traffic light control system using Embedded C and Arduino IDE.</li>
            <li>Simulated real-time traffic operations through programmed timing sequences and hardware interfacing.</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-wrap">
    <div class="section-eyebrow sr"><span class="eyebrow-line"></span> Projects</div>
    <h2 class="section-heading sr">Things I've <span class="accent-v">built</span></h2>
    <div class="projects-grid sr">
      <div class="project-card">
        <div class="project-num">01</div>
        <div class="project-icon">🌿</div>
        <div class="project-title">IoT Wild Animal Intrusion Detection &amp; Alert System</div>
        <p class="project-desc">An IoT monitoring solution for detecting wild animal intrusions near agricultural land. Combines sensor networks with image processing for real-time alerts and automated monitoring to protect crops and farmers from wildlife damage.</p>
        <div class="project-tags">
          <span class="project-tag">IoT</span>
          <span class="project-tag">Image Processing</span>
          <span class="project-tag">Sensors</span>
          <span class="project-tag">Real-time Alerts</span>
          <span class="project-tag">Agriculture Safety</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-num">02</div>
        <div class="project-icon">🚦</div>
        <div class="project-title">ESP32 Traffic Light Control System</div>
        <p class="project-desc">A hardware-software system built with the ESP32 microcontroller using Embedded C to simulate real-time traffic light operations. Programmed timing sequences and hardware interfacing for realistic traffic simulation with configurable durations.</p>
        <div class="project-tags">
          <span class="project-tag">ESP32</span>
          <span class="project-tag">Embedded C</span>
          <span class="project-tag">Arduino IDE</span>
          <span class="project-tag">Hardware Interfacing</span>
          <span class="project-tag">Wokwi</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- SKILLS -->
<section id="skills">
  <div class="section-wrap">
    <div class="section-eyebrow sr"><span class="eyebrow-line"></span> Skills</div>
    <h2 class="section-heading sr">Technical <span class="accent">arsenal</span></h2>
    <div class="skills-layout">
      <div class="sr">
        <div class="skill-group">
          <div class="skill-group-label">Programming Languages</div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Python</span><span class="skill-pct">85%</span></div><div class="skill-track"><div class="skill-fill" data-w="85"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Embedded C</span><span class="skill-pct">80%</span></div><div class="skill-track"><div class="skill-fill" data-w="80"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">C (Basic)</span><span class="skill-pct">60%</span></div><div class="skill-track"><div class="skill-fill" data-w="60"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Java (Basic)</span><span class="skill-pct">50%</span></div><div class="skill-track"><div class="skill-fill" data-w="50"></div></div></div>
        </div>
        <div class="skill-group">
          <div class="skill-group-label">Hardware &amp; Protocols</div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">CAN Communication</span><span class="skill-pct">85%</span></div><div class="skill-track"><div class="skill-fill v" data-w="85"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Arduino / ESP32</span><span class="skill-pct">80%</span></div><div class="skill-track"><div class="skill-fill v" data-w="80"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Embedded Systems</span><span class="skill-pct">78%</span></div><div class="skill-track"><div class="skill-fill v" data-w="78"></div></div></div>
          <div class="skill-bar-item"><div class="skill-bar-header"><span class="skill-name">Pin Mapping / MCU</span><span class="skill-pct">75%</span></div><div class="skill-track"><div class="skill-fill v" data-w="75"></div></div></div>
        </div>
      </div>
      <div class="sr" style="transition-delay:0.15s">
        <div class="skill-group">
          <div class="skill-group-label">Tools &amp; Platforms</div>
          <div class="tech-grid">
            <div class="tech-chip">IoT Dev</div>
            <div class="tech-chip">Wokwi</div>
            <div class="tech-chip">MATLAB</div>
            <div class="tech-chip">Validation</div>
            <div class="tech-chip">MS Office</div>
            <div class="tech-chip">Arduino IDE</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- CERTIFICATIONS -->
<section id="certifications">
  <div class="section-wrap">
    <div class="section-eyebrow sr"><span class="eyebrow-line"></span> Certifications</div>
    <h2 class="section-heading sr">Credentials &amp; <span class="accent">training</span></h2>
    <div class="certs-grid sr">
      <div class="cert-card">
        <div class="cert-badge-wrap">NPT</div>
        <div class="cert-name">Python for Data Science</div>
        <div class="cert-issuer">NPTEL</div>
      </div>
      <div class="cert-card">
        <div class="cert-badge-wrap">NPT</div>
        <div class="cert-name">Ethics in Engineering Practice</div>
        <div class="cert-issuer">NPTEL</div>
      </div>
      <div class="cert-card">
        <div class="cert-badge-wrap">WRK</div>
        <div class="cert-name">Art of Communication Workshop</div>
        <div class="cert-issuer">Workshop Certification</div>
      </div>
      <div class="cert-card">
        <div class="cert-badge-wrap">IOT</div>
        <div class="cert-name">AI &amp; IoT Bootcamp</div>
        <div class="cert-issuer">Bootcamp Certification</div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- CONTACT -->
<section id="contact">
  <div class="section-wrap">
    <div class="contact-grid">
      <div class="sr-left">
        <div class="section-eyebrow"><span class="eyebrow-line"></span> Contact</div>
        <div class="avail"><span class="avail-pulse"></span>Open to opportunities</div>
        <h2><span class="g">Let's build<br>something real.</span></h2>
        <p>Looking for entry-level roles in embedded systems, automotive engineering, and IoT. Based in Ramanathapuram, Tamil Nadu — open to relocation.</p>

        <p style="margin-bottom:20px;"></p>
        <a href="mailto:nagarathinamjeeva7@gmail.com" class="btn-primary">Send a Message</a>
       
        <!-- RESUME DOWNLOAD -->
        <a href="data:application/pdf;base64,JVBERi0xLjQKJfbk/N8KMSAwIG9iago8PAovVHlwZSAvQ2F0YWxvZwovVmVyc2lvbiAvMS40Ci9QYWdlcyAyIDAgUgovTWV0YWRhdGEgMyAwIFIKL1N0cnVjdFRyZWVSb290IDQgMCBSCi9NYXJrSW5mbyA1IDAgUgovTGFuZyAoZW4pCi9WaWV3ZXJQcmVmZXJlbmNlcyA2IDAgUgovT3V0bGluZXMgNyAwIFIKL091dHB1dEludGVudHMgWzggMCBSXQo+PgplbmRvYmoKOSAwIG9iago8PAovVGl0bGUgKEJsYWNrIGFuZCBXaGl0ZSBNaW5pbWFsaXN0IFByb2Zlc3Npb25hbCBSZXN1bWUgQTQpCi9DcmVhdG9yIChDYW52YSkKL1Byb2R1Y2VyIChDYW52YSkKL0NyZWF0aW9uRGF0ZSAoRDoyMDI2MDYyNDA4Mzg0MiswMCcwMCcpCi9Nb2REYXRlIChEOjIwMjYwNjI0MDgzODQyKzAwJzAwJykKL0tleXdvcmRzIChEQUhMZjdUMEJpMCxCQUdza1dtZE05dywwKQovQXV0aG9yIChOLiBKRUVWQSkKL1RyYXBwZWQgL0ZhbHNlCj4+CmVuZG9iagoyIDAgb2JqCjw8Ci9UeXBlIC9QYWdlcwovS2lkcyBbMTAgMCBSXQovQ291bnQgMQo+PgplbmRvYmoKMyAwIG9iago8PAovTGVuZ3RoIDMxMzgKL1R5cGUgL01ldGFkYXRhCi9TdWJ0eXBlIC9YTUwKPj4Kc3RyZWFtDQo8P3hwYWNrZXQgYmVnaW49Iu+7vyIgaWQ9Ilc1TTBNcENlaGlIenJlU3pOVGN6a2M5ZCI/Pgo8cmRmOlJERiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogIDxyZGY6RGVzY3JpcHRpb24gcmRmOmFib3V0PSIiCiAgICAgIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIKICAgICAgeG1sbnM6cGRmPSJodHRwOi8vbnMuYWRvYmUuY29tL3BkZi8xLjMvIgogICAgICB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iCiAgICAgIHhtbG5zOnBkZnVhaWQ9Imh0dHA6Ly93d3cuYWlpbS5vcmcvcGRmdWEvbnMvaWQvIgogICAgZGM6bGFuZ3VhZ2U9ImVuIgogICAgZGM6Zm9ybWF0PSJhcHBsaWNhdGlvbi9wZGYiCiAgICBwZGY6UHJvZHVjZXI9IkNhbnZhIgogICAgcGRmOktleXdvcmRzPSJEQUhMZjdUMEJpMCxCQUdza1dtZE05dywwIgogICAgcGRmOlRyYXBwZWQ9IkZhbHNlIgogICAgeG1wOkNyZWF0b3JUb29sPSJDYW52YSIKICAgIHhtcDpDcmVhdGVEYXRlPSIyMDI2LTA2LTI0VDA4OjM4OjQyLjQ0MVoiCiAgICB4bXA6TW9kaWZ5RGF0ZT0iMjAyNi0wNi0yNFQwODozODo0Mi40NDFaIgogICAgeG1wOk1ldGFkYXRhRGF0ZT0iMjAyNi0wNi0yNFQwODozODo0Mi40NDFaIgogICAgcGRmdWFpZDpwYXJ0PSIxIj4KICAgIDxkYzp0aXRsZT4KICAgICAgPHJkZjpBbHQ+CiAgICAgICAgPHJkZjpsaSB4bWw6bGFuZz0ieC1kZWZhdWx0Ij5CbGFjayBhbmQgV2hpdGUgTWluaW1hbGlzdCBQcm9mZXNzaW9uYWwgUmVzdW1lIEE0PC9yZGY6bGk+CiAgICAgICAgPHJkZjpsaSB4bWw6bGFuZz0iZW4iPkJsYWNrIGFuZCBXaGl0ZSBNaW5pbWFsaXN0IFByb2Zlc3Npb25hbCBSZXN1bWUgQTQ8L3JkZjpsaT4KICAgICAgPC9yZGY6QWx0PgogICAgPC9kYzp0aXRsZT4KICAgIDxkYzpjcmVhdG9yPgogICAgICA8cmRmOlNlcT4KICAgICAgICA8cmRmOmxpPk4uIEpFRVZBPC9yZGY6bGk+CiAgICAgIDwvcmRmOlNlcT4KICAgIDwvZGM6Y3JlYXRvcj4KICA8L3JkZjpEZXNjcmlwdGlvbj4KPC9yZGY6UkRGPgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgCjw/eHBhY2tldCBlbmQ9InciPz4NCmVuZHN0cmVhbQplbmRvYmoKNCAwIG9iago8PAovVHlwZSAvU3RydWN0VHJlZVJvb3QKL0sgWzExIDAgUl0KL1BhcmVudFRyZWUgMTIgMCBSCi9QYXJlbnRUcmVlTmV4dEtleSAxCi9JRFRyZWUgMTMgMCBSCj4+CmVuZG9iago1IDAgb2JqCjw8Ci9NYXJrZWQgdHJ1ZQo+PgplbmRvYmoKNiAwIG9iago8PAovVHlwZSAvVmlld2VyUHJlZmVyZW5jZXMKL0Rpc3BsYXlEb2NUaXRsZSB0cnVlCj4+CmVuZG9iago3IDAgb2JqCjw8Ci9UeXBlIC9PdXRsaW5lcwo+PgplbmRvYmoKOCAwIG9iago8PAovSW5mbyAoc1JHQiBJRUM2MTk2Ni0yLjEpCi9PdXRwdXRDb25kaXRpb24gKHNSR0IpCi9PdXRwdXRDb25kaXRpb25JZGVudGlmaWVyIChJRUMgNjE5NjYtMi0xOjE5OTkpCi9SZWdpc3RyeU5hbWUgKGh0dHA6Ly93d3cuY29sb3Iub3JnKQovRGVzdE91dHB1dFByb2ZpbGUgMTQgMCBSCj4+CmVuZG9iagoxMCAwIG9iago8PAovVHlwZSAvUGFnZQovUmVzb3VyY2VzIDw8Ci9Qcm9jU2V0IFsvUERGIC9UZXh0IC9JbWFnZUIgL0ltYWdlQyAvSW1hZ2VJXQovRXh0R1N0YXRlIDE1IDAgUgovWE9iamVjdCA8PAovWDExIDE2IDAgUgo+Pgo+PgovTWVkaWFCb3ggWzAuMCA3LjgyOTk4MTMgNTk1LjUgODUwLjA3OTk2XQovQ29udGVudHMgMTcgMCBSCi9TdHJ1Y3RQYXJlbnRzIDAKL1RhYnMgL1MKL1BhcmVudCAyIDAgUgovQmxlZWRCb3ggWzAuMCA3LjgyOTk4MTMgNTk1LjUgODUwLjA3OTk2XQovVHJpbUJveCBbMC4wIDcuODI5OTgxMyA1OTUuNSA4NTAuMDc5OTZdCi9Dcm9w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YmoKMjEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgOTAgMCBSCi9FIChJbXByb3ZlZCB2YWxpZGF0aW9uIGVmZmljaWVuY3kgYnkgZGV2ZWxvcGluZyBQeXRob24gYXV0b21hdGlvbiBzY3JpcHRzIGZvciBhdXRvbW90aXZlIGRpZ2l0YWwgY2x1c3RlciB0ZXN0aW5nLikKL1BnIDEwIDAgUgovSyBbMl0KPj4KZW5kb2JqCjIyIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDkxIDAgUgovRSAoRW5oYW5jZWQgYWNjdXJhY3kgYnkgYXV0b21hdGluZyBDQU4gbWVzc2FnZSBkZWNvZGluZywgbG9nIHBhcnNpbmcsIGFuZCBzaWduYWwgdmVyaWZpY2F0aW9uLikKL1BnIDEwIDAgUgovSyBbM10KPj4KZW5kb2JqCjIzIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDkyIDAgUgovRSAoR2VuZXJhdGVkIGF1dG9tYXRlZCB2YWxpZGF0aW9uIHJlcG9ydHMgYW5kIHJlZHVjZWQgbWFudWFsIGVmZm9ydCB0aHJvdWdoIHJlcGVhdGFibGUgd29ya2Zsb3dzLikKL1BnIDEwIDAgUgovSyBbNF0KPj4KZW5kb2JqCjI0IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSA8NTA1MjQ5NDM0RjRDMjA0QzQ5NEQ0OTU0NDU0NDIwODUyMDUyNDY1MTIwNTQ2NTYzNjg2RTY5NjM2MTZDMjA1MDcyNkY3MDZGNzM2MTZDMjAyNjIwNDg2MTcyNjQ3NzYxNzI2NTIwNDQ2NTczNjk2NzZFMjA0OTZFNzQ2NTcyNkU+Ci9QZyAxMCAwIFIKL0sgWzVdCj4+CmVuZG9iagoyNSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCA5MyAwIFIKL0UgKFN1cHBvcnRlZCBSRlEgcHJvcG9zYWwgcHJlcGFyYXRpb24gdGhyb3VnaCByZXF1aXJlbWVudCBjb21wYXJpc29uIGFuZCB0ZWNobmljYWwgYW5hbHlzaXMuKQovUGcgMTAgMCBSCi9LIFs2XQo+PgplbmRvYmoKMjYgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgOTQgMCBSCi9FIChBc3Npc3RlZCB3aXRoIGhhcmR3YXJlIGRlc2lnbiBsZWFybmluZyBhbmQgcHJvZHVjdCBkZXZlbG9wbWVudCBhY3Rpdml0aWVzLikKL1BnIDEwIDAgUgovSyBbN10KPj4KZW5kb2JqCjI3IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSA8NTI0NTU0NDU0MzQ4MjA1MzRGNEM1NTU0NDk0RjRFNTMyMDUwNTY1NDJFMjA0QzU0NDQyRTIwODUyMDQ1NkQ2MjY1NjQ2NDY1NjQyMDUzNzk3Mzc0NjU2RDczMjA0OTZFNzQ2NTcyNkU+Ci9QZyAxMCAwIFIKL0sgWzhdCj4+CmVuZG9iagoyOCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCA5NSAwIFIKL0UgKERldmVsb3BlZCBhbiBFU1AzMi1iYXNlZCB0cmFmZmljIGxpZ2h0IGNvbnRyb2wgc3lzdGVtIHVzaW5nIEVtYmVkZGVkIEMgYW5kIEFyZHVpbm8gSURFLikKL1BnIDEwIDAgUgovSyBbOV0KPj4KZW5kb2JqCjI5IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDk2IDAgUgovRSAoU2ltdWxhdGVkIHJlYWwtdGltZSB0cmFmZmljIG9wZXJhdGlvbnMgdGhyb3VnaCBwcm9ncmFtbWVkIHRpbWluZyBzZXF1ZW5jZXMgYW5kIGhhcmR3YXJlIGludGVyZmFjaW5nLikKL1BnIDEwIDAgUgovSyBbMTBdCj4+CmVuZG9iagozMCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKElvVC1CYXNlZCBXaWxkIEFuaW1hbCBJbnRydXNpb24gRGV0ZWN0aW9uIGFuZCBBbGVydCBTeXN0ZW0pCi9QZyAxMCAwIFIKL0sgWzExXQo+PgplbmRvYmoKMzEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgOTcgMCBSCi9FIChEZXZlbG9wZWQgYW4gSW9UIG1vbml0b3Jpbmcgc29sdXRpb24gZm9yIGRldGVjdGluZyB3aWxkIGFuaW1hbCBpbnRydXNpb25zIHVzaW5nIHNlbnNvcnMgYW5kIGltYWdlIHByb2Nlc3NpbmcuKQovUGcgMTAgMCBSCi9LIFsxMl0KPj4KZW5kb2JqCjMyIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDk4IDAgUgovRSAoSW1wbGVtZW50ZWQgcmVhbC10aW1lIGFsZXJ0cyBhbmQgYXV0b21hdGVkIG1vbml0b3JpbmcgZm9yIGFncmljdWx0dXJhbCBzYWZldHkuKQovUGcgMTAgMCBSCi9LIFsxM10KPj4KZW5kb2JqCjMzIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9GaWd1cmUKL1AgMTggMCBSCi9QZyAxMCAwIFIKL0EgWzk5IDAgUiAwXQovSyBbMTRdCj4+CmVuZG9iagozNCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKEpFRVZBIE4pCi9QZyAxMCAwIFIKL0sgWzE1XQo+PgplbmRvYmoKMzUgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTggMCBSCi9FIChDQVJFRVIgT0JKRUNUSVZFKQovUGcgMTAgMCBSCi9LIFsxNl0KPj4KZW5kb2JqCjM2IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSAoRWxlY3Ryb25pY3MgYW5kIENvbW11bmljYXRpb24gRW5naW5lZXJpbmcgdW5kZXJncmFkdWF0ZSB3aXRoIGV4cGVyaWVuY2UgaW4gRW1iZWRkZWQgU3lzdGVtcywgQXV0b21vdGl2ZSBWYWxpZGF0aW9uLCBQeXRob24gQXV0b21hdGlvbiwgSW9ULCBhbmQgQ0FOIGNvbW11bmljYXRpb24uIFNlZWtpbmcgYW4gZW50cnktbGV2ZWwgcm9sZSB0byBjb250cmlidXRlIHRvIGVtYmVkZGVkIGFuZCBhdXRvbW90aXZlIGVuZ2luZWVyaW5nIHByb2plY3RzIHdoaWxlIGV4cGFuZGluZyB0ZWNobmljYWwgZXhwZXJ0aXNlLikKL1BnIDEwIDAgUgovSyBbMTddCj4+CmVuZG9iagozNyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKCs5MSA3OTA0MTQ1NzU3KQovUGcgMTAgMCBSCi9LIFsxOF0KPj4KZW5kb2JqCjM4IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSAobmFnYXJhdGhpbmFtamVldmE3QGdtYWlsLmNvbSkKL1BnIDEwIDAgUgovSyBbMTldCj4+CmVuZG9iagozOSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKEVEVUNBVElPTikKL1BnIDEwIDAgUgovSyBbMjBdCj4+CmVuZG9iago0MCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKCBJTlRFUk5TSElQIEVYUEVSSUVOQ0UpCi9QZyAxMCAwIFIKL0sgWzIxXQo+PgplbmRvYmoKNDEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTggMCBSCi9FIChTS0lMTFMpCi9QZyAxMCAwIFIKL0sgWzIyXQo+PgplbmRvYmoKNDIgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTAwIDAgUgovRSAoUHl0aG9uKQovUGcgMTAgMCBSCi9LIFsyM10KPj4KZW5kb2JqCjQzIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDEwMSAwIFIKL0UgKGMgXChCYXNpY1wpKQovUGcgMTAgMCBSCi9LIFsyNF0KPj4KZW5kb2JqCjQ0IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDEwMiAwIFIKL0UgKEphdmEgXChCYXNpY1wpKQovUGcgMTAgMCBSCi9LIFsyNV0KPj4KZW5kb2JqCjQ1IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDEwMyAwIFIKL0UgKEFyZHVpbm8pCi9QZyAxMCAwIFIKL0sgWzI2XQo+PgplbmRvYmoKNDYgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTA0IDAgUgovRSAoRW1iZWRkZWQgU3lzdGVtcykKL1BnIDEwIDAgUgovSyBbMjddCj4+CmVuZG9iago0NyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxMDUgMCBSCi9FIChDQU4gY29tbXVuaWNhdGlvbikKL1BnIDEwIDAgUgovSyBbMjhdCj4+CmVuZG9iago0OCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxMDYgMCBSCi9FIChWYWxpZGF0aW9uIFRlc3RpbmcpCi9QZyAxMCAwIFIKL0sgWzI5XQo+PgplbmRvYmoKNDkgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTA3IDAgUgovRSAoSW9ULCBXb2t3aSwgTUFUTEFCKQovUGcgMTAgMCBSCi9LIFszMF0KPj4KZW5kb2JqCjUwIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDEwOCAwIFIKL0UgKE1pY3Jvc29mdCBPZmZpY2UpCi9QZyAxMCAwIFIKL0sgWzMxXQo+PgplbmRvYmoKNTEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTA5IDAgUgovRSAoUGluIE1hcHBpbmcgaW4gTWljcm9jb250cm9sbGVyKQovUGcgMTAgMCBSCi9LIFszMl0KPj4KZW5kb2JqCjUyIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSAoMy83MDZEU2FndWwgSGFtaWV0aHUgc3RyZWV0LCkKL1BnIDEwIDAgUgovSyBbMzNdCj4+CmVuZG9iago1MyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKCBQYXJhbWFrdWRpLFJhbWFuYXRoYXB1cmFtKQovUGcgMTAgMCBSCi9LIFszNF0KPj4KZW5kb2JqCjU0IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9QCi9QIDE4IDAgUgovRSAoUFJPSkVDVFMpCi9QZyAxMCAwIFIKL0sgWzM1XQo+PgplbmRvYmoKNTUgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTggMCBSCi9FIChDRVJUSUZJQ0FUSU9OUykKL1BnIDEwIDAgUgovSyBbMzZdCj4+CmVuZG9iago1NiAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxMTAgMCBSCi9FIChQeXRob24gZm9yIERhdGEgU2NpZW5jZSBcKE5QVEVMXCkpCi9QZyAxMCAwIFIKL0sgWzM3XQo+PgplbmRvYmoKNTcgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL1AKL1AgMTExIDAgUgovRSAoRXRoaWNzIGluIEVuZ2luZWVyaW5nIFByYWN0aWNlIFwoTlBURUxcKSkKL1BnIDEwIDAgUgovSyBbMzhdCj4+CmVuZG9iago1OCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxMTIgMCBSCi9FIChBcnQgb2YgQ29tbXVuaWNhdGlvbiBXb3Jrc2hvcCkKL1BnIDEwIDAgUgovSyBbMzldCj4+CmVuZG9iago1OSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxMTMgMCBSCi9FIChBSSAmIElvVCBCb290Y2FtcCkKL1BnIDEwIDAgUgovSyBbNDBdCj4+CmVuZG9iago2MCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKGh0dHBzOi8vd3d3LmxpbmtlZGluLmNvbS9pbi9uLWplZXZhLTUwMjZiYjI5NSkKL1BnIDEwIDAgUgovSyBbNDFdCj4+CmVuZG9iago2MSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvUAovUCAxOCAwIFIKL0UgKGh0dHBzOi8vbmFnYXJhdGhpbmFtamVldmEuZ2l0aHViLmlvL0pFRVZBLk4vKQovUGcgMTAgMCBSCi9LIFs0Ml0KPj4KZW5kb2JqCjYyIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9GaWd1cmUKL1AgMTggMCBSCi9QZyAxMCAwIFIKL0EgWzExNCAwIFIgMF0KL0sgWzQzXQo+PgplbmRvYmoKNjMgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0ZpZ3VyZQovUCAxOCAwIFIKL1BnIDEwIDAgUgovQSBbMTE1IDAgUiAwXQovSyBbNDRdCj4+CmVuZG9iago2NCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvRmlndXJlCi9QIDE4IDAgUgovUGcgMTAgMCBSCi9BIFsxMTYgMCBSIDBdCi9LIFs0NV0KPj4KZW5kb2JqCjY1IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9GaWd1cmUKL1AgMTggMCBSCi9QZyAxMCAwIFIKL0EgWzExNyAwIFIgMF0KL0sgWzQ2XQo+PgplbmRvYmoKNjYgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0ZpZ3VyZQovUCAxOCAwIFIKL1BnIDEwIDAgUgovQSBbMTE4IDAgUiAwXQovSyBbNDddCj4+CmVuZG9iago2NyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvRmlndXJlCi9QIDE4IDAgUgovUGcgMTAgMCBSCi9BIFsxMTkgMCBSIDBdCi9LIFs0OF0KPj4KZW5kb2JqCjY4IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9GaWd1cmUKL1AgMTggMCBSCi9QZyAxMCAwIFIKL0EgWzEyMCAwIFIgMF0KL0sgWzQ5XQo+PgplbmRvYmoKNjkgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0ZpZ3VyZQovUCAxOCAwIFIKL1BnIDEwIDAgUgovQSBbMTIxIDAgUiAwXQovSyBbNTBdCj4+CmVuZG9iago3MCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvRmlndXJlCi9QIDE4IDAgUgovUGcgMTAgMCBSCi9BIFsxMjIgMCBSIDBdCi9LIFs1MV0KPj4KZW5kb2JqCjcxIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9GaWd1cmUKL1AgMTggMCBSCi9QZyAxMCAwIFIKL0EgWzEyMyAwIFIgMF0KL0sgWzUyXQo+PgplbmRvYmoKNzIgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0ZpZ3VyZQovUCAxOCAwIFIKL1BnIDEw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ZSAvU3RydWN0RWxlbQovUyAvTAovUCAxOCAwIFIKL0sgWzE1MCAwIFIgMTUxIDAgUiAxNTIgMCBSIDE1MyAwIFJdCi9QZyAxMCAwIFIKPj4KZW5kb2JqCjg5IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MCi9QIDE4IDAgUgovSyBbMTU0IDAgUiAxNTUgMCBSIDE1NiAwIFJdCi9QZyAxMCAwIFIKPj4KZW5kb2JqCjkwIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MQm9keQovUCAxMzQgMCBSCi9LIDIxIDAgUgo+PgplbmRvYmoKOTEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDEzNSAwIFIKL0sgMjIgMCBSCj4+CmVuZG9iago5MiAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEJvZHkKL1AgMTM2IDAgUgovSyAyMyAwIFIKPj4KZW5kb2JqCjkzIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MQm9keQovUCAxMzcgMCBSCi9LIDI1IDAgUgo+PgplbmRvYmoKOTQgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDEzOCAwIFIKL0sgMjYgMCBSCj4+CmVuZG9iago5NSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEJvZHkKL1AgMTM5IDAgUgovSyAyOCAwIFIKPj4KZW5kb2JqCjk2IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MQm9keQovUCAxNDAgMCBSCi9LIDI5IDAgUgo+PgplbmRvYmoKOTcgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0MSAwIFIKL0sgMzEgMCBSCj4+CmVuZG9iago5OCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEJvZHkKL1AgMTQyIDAgUgovSyAzMiAwIFIKPj4KZW5kb2JqCjk5IDAgb2JqCjw8Ci9PIC9MYXlvdXQKL0JCb3ggWzI4My4xNzc4IDc2NC4xMTk0IDI5OC4xODM0NCA3NzkuMTI1MDZdCi9QbGFjZW1lbnQgL0Jsb2NrCj4+CmVuZG9iagoxMDAgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0NyAwIFIKL0sgNDIgMCBSCj4+CmVuZG9iagoxMDEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0OCAwIFIKL0sgNDMgMCBSCj4+CmVuZG9iagoxMDIgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0OSAwIFIKL0sgNDQgMCBSCj4+CmVuZG9iagoxMDMgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1MCAwIFIKL0sgNDUgMCBSCj4+CmVuZG9iagoxMDQgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1MSAwIFIKL0sgNDYgMCBSCj4+CmVuZG9iagoxMDUgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1MiAwIFIKL0sgNDcgMCBSCj4+CmVuZG9iagoxMDYgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1MyAwIFIKL0sgNDggMCBSCj4+CmVuZG9iagoxMDcgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1NCAwIFIKL0sgNDkgMCBSCj4+CmVuZG9iagoxMDggMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1NSAwIFIKL0sgNTAgMCBSCj4+CmVuZG9iagoxMDkgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE1NiAwIFIKL0sgNTEgMCBSCj4+CmVuZG9iagoxMTAgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0MyAwIFIKL0sgNTYgMCBSCj4+CmVuZG9iagoxMTEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0NCAwIFIKL0sgNTcgMCBSCj4+CmVuZG9iagoxMTIgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0NSAwIFIKL0sgNTggMCBSCj4+CmVuZG9iagoxMTMgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xCb2R5Ci9QIDE0NiAwIFIKL0sgNTkgMCBSCj4+CmVuZG9iagoxMTQgMCBvYmoKPDwKL08gL0xheW91dAovQkJveCBbNjAuMDQ4NDU0IDc4Mi44Mzc2IDY5LjQyNTU2IDc5Mi4yMzE3NV0KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjExNSAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFs2MS4xOTY0NCA3NDkuNTYyOCA2OS40MjU1NiA3NjIuMDY1Nl0KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjExNiAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFsyODUuMDE1MzIgNzg0LjUxNjk3IDI5NC4zOTI0MyA3OTAuNTUyNF0KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjExNyAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFsyODUuMDE1MzIgNzQ1LjAxMTE3IDI5NS44MTgzMyA3NTUuODE0MTVdCi9QbGFjZW1lbnQgL0Jsb2NrCj4+CmVuZG9iagoxMTggMCBvYmoKPDwKL08gL0xheW91dAovQkJveCBbNTkuNTI3NTU3IDczNi4wMTExNyA1MzUuNzQ4MDUgNzM2Ljc2MTE3XQovUGxhY2VtZW50IC9CbG9jawo+PgplbmRvYmoKMTE5IDAgb2JqCjw8Ci9PIC9MYXlvdXQKL0JCb3ggWzU5LjUyNzU1NyA2MzguMTk0MzQgNTM1Ljc0ODA1IDYzOC45NDQzNF0KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjEyMCAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFs1NS43NzkwNjggNTY2LjI2NTkgNTM1Ljc0ODA1IDU3Ni45MTU5NV0KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjEyMSAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFs2MS4xOTY0NCAzMzguMTY1OTIgNTQxLjE2NTQgMzM4LjkxNTkyXQovUGxhY2VtZW50IC9CbG9jawo+PgplbmRvYmoKMTIyIDAgb2JqCjw8Ci9PIC9MYXlvdXQKL0JCb3ggWzY0LjczNzAxIDI0NC4xNjU5NyA1NDQuNzA2IDI0NC45MTU5N10KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjEyMyAwIG9iago8PAovTyAvTGF5b3V0Ci9CQm94IFs1Ny42NTMzMTMgMTgwLjE4MTMyIDUzNy42MjIyNSAxODAuOTMxMzJdCi9QbGFjZW1lbnQgL0Jsb2NrCj4+CmVuZG9iagoxMjQgMCBvYmoKPDwKL08gL0xheW91dAovQkJveCBbLTIyLjA2NTEyNiAtNDIuMzYwMjQ1IDYxNy4zNDA3IDI4LjM5MDM0M10KL1BsYWNlbWVudCAvQmxvY2sKPj4KZW5kb2JqCjEyNSAwIG9iago8PAovQ0EgMQovY2EgMQovTEMgMAovTEogMAovTFcgMQovTUwgNAovU0EgdHJ1ZQovQk0gL05vcm1hbAo+PgplbmRvYmoKMTI2IDAgb2JqCjw8Ci9HMyA3MyAwIFIKPj4KZW5kb2JqCjEyNyAwIG9iago8PAovVHlwZSAvR3JvdXAKL1MgL1RyYW5zcGFyZW5jeQovSSB0cnVlCj4+CmVuZG9iagoxMjggMCBvYmoKPDwKL0xlbmd0aCAyOTMKL04gMwovRmlsdGVyIC9GbGF0ZURlY29kZQo+PgpzdHJlYW0NCnicfZC9SsMAFIW/1IIoioMOHRwyOLhok6ZpUnBpIhbXVqGpU5KmQexPSFP0AXRzcHUrLr6A6GMoCA7i4COIoLOkQVKQeODCx+HAvfdArgCQl6A/iMJG3RBbVlucf0dAYCrbHQVkS4DvlyT7vPVPLksLHW/kAh9AFLasNggdYM1P+CxmJ+HLmE+jIAJhEnN40DBBuAM2/Rl2ZtgNwjj/Buz0e2M3vZslb3DYBFrAOnWGDPHp4VGkyQnH2BTRMFHZo0YJGRUZhSoa5enUkCijU8HAwMRER0FDQWEXlWrcZ7JyeAP6F8xdpZ5zDQ8XUHhNvY0JrJzD/WPqpR0HdmhPrTyQ63bh8xaWLVh9gsWj32IzfhX//CqyzwCXbURKSMhUfgCFzUu9DQplbmRzdHJlYW0KZW5kb2JqCjEyOSAwIG9iago8PAovRzMgNzMgMCBSCj4+CmVuZG9iagoxMzAgMCBvYmoKPDwKL0Y5IDEzMyAwIFIKPj4KZW5kb2JqCjEzMSAwIG9iago8PAovVHlwZSAvR3JvdXAKL1MgL1RyYW5zcGFyZW5jeQovSSB0cnVlCj4+CmVuZG9iagoxMzIgMCBvYmoKPDwKL1R5cGUgL0ZvbnQKL1N1YnR5cGUgL1R5cGUwCi9CYXNlRm9udCAvQUFBQUFBK0dhcmV0LVJlZ3VsYXIKL0VuY29kaW5nIC9JZGVudGl0eS1ICi9EZXNjZW5kYW50Rm9udHMgWzE1NyAwIFJdCi9Ub1VuaWNvZGUgMTU4IDAgUgo+PgplbmRvYmoKMTMzIDAgb2JqCjw8Ci9UeXBlIC9Gb250Ci9TdWJ0eXBlIC9UeXBlMAovQmFzZUZvbnQgL0JBQUFBQStHYXJldC1Cb2xkCi9FbmNvZGluZyAvSWRlbnRpdHktSAovRGVzY2VuZGFudEZvbnRzIFsxNTkgMCBSXQovVG9Vbmljb2RlIDE2MCAwIFIKPj4KZW5kb2JqCjEzNCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODEgMCBSCi9LIFs5MCAwIFJdCj4+CmVuZG9iagoxMzUgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDgxIDAgUgovSyBbOTEgMCBSXQo+PgplbmRvYmoKMTM2IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4MSAwIFIKL0sgWzkyIDAgUl0KPj4KZW5kb2JqCjEzNyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODIgMCBSCi9LIFs5MyAwIFJdCj4+CmVuZG9iagoxMzggMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDgyIDAgUgovSyBbOTQgMCBSXQo+PgplbmRvYmoKMTM5IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4MyAwIFIKL0sgWzk1IDAgUl0KPj4KZW5kb2JqCjE0MCAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODMgMCBSCi9LIFs5NiAwIFJdCj4+CmVuZG9iagoxNDEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDg0IDAgUgovSyBbOTcgMCBSXQo+PgplbmRvYmoKMTQyIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4NCAwIFIKL0sgWzk4IDAgUl0KPj4KZW5kb2JqCjE0MyAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODUgMCBSCi9LIFsxMTAgMCBSXQo+PgplbmRvYmoKMTQ0IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4NSAwIFIKL0sgWzExMSAwIFJdCj4+CmVuZG9iagoxNDUgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDg2IDAgUgovSyBbMTEyIDAgUl0KPj4KZW5kb2JqCjE0NiAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODYgMCBSCi9LIFsxMTMgMCBSXQo+PgplbmRvYmoKMTQ3IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4NyAwIFIKL0sgWzEwMCAwIFJdCj4+CmVuZG9iagoxNDggMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDg3IDAgUgovSyBbMTAxIDAgUl0KPj4KZW5kb2JqCjE0OSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODcgMCBSCi9LIFsxMDIgMCBSXQo+PgplbmRvYmoKMTUwIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4OCAwIFIKL0sgWzEwMyAwIFJdCj4+CmVuZG9iagoxNTEgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDg4IDAgUgovSyBbMTA0IDAgUl0KPj4KZW5kb2JqCjE1MiAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODggMCBSCi9LIFsxMDUgMCBSXQo+PgplbmRvYmoKMTUzIDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4OCAwIFIKL0sgWzEwNiAwIFJdCj4+CmVuZG9iagoxNTQgMCBvYmoKPDwKL1R5cGUgL1N0cnVjdEVsZW0KL1MgL0xJCi9QIDg5IDAgUgovSyBbMTA3IDAgUl0KPj4KZW5kb2JqCjE1NSAwIG9iago8PAovVHlwZSAvU3RydWN0RWxlbQovUyAvTEkKL1AgODkgMCBSCi9LIFsxMDggMCBSXQo+PgplbmRvYmoKMTU2IDAgb2JqCjw8Ci9UeXBlIC9TdHJ1Y3RFbGVtCi9TIC9MSQovUCA4OSAwIFIKL0sgWzEwOSAwIFJdCj4+CmVuZG9iagoxNTcgMCBvYmoKPDwKL1R5cGUgL0ZvbnQKL0ZvbnREZXNjcmlwdG9yIDE2MSAwIFIKL0Jhc2VGb250IC9BQUFBQUErR2FyZXQtUmVndWxhcgovU3VidHlwZSAvQ0lERm9udFR5cGUyCi9DSURUb0dJRE1hcCAvSWRlbnRpdHkKL0NJRFN5c3RlbUluZm8gMTYyIDAgUgovVyBbMCBbODcwIDAgMjQ4XQogMTYgWzY3MSA4MTZdCiAyMyBbNzYxIDAgMCAwIDYwM10KIDM3IFs1NTggODI1XQogNDQgWzc1MSAwIDAgMjkyXQo1OCBbNDgwXQogNjMgWzU2MV0KIDY5IFs5MTYgNzYwXQogNzYgWzg0MF0KIDg4IFs2MzkgMCA4NDAgNjgxIDAgMCAwIDY0N10KMTAzIFs2MzBdCiAxMDggWzcyOV0KIDExOSBbNjczIDEwNzhdCiAxMzkgWzYyMF0KIDE1MyBbNjM0XQoxNjMgWzYzNl0KIDE3NCBbNDIzIDY3NF0KIDE4MSBbNjU3IDAgMCAyNzBdCiAxOTYgWzI2OSAwIDAgMCA1ODMgMCAwIDI3MF0KIDIwOSBbMTAxMiA2NTddCjIxNyBbNjU0XQogMjMyIFs0MzYgMCAwIDAgNTQ2XQogMjQ0IFs0NDRdCiAyNDkgWzY1Ml0KIDI2MCBbNTY4IDg2OF0KMjY2IFs1NzcgNTY4XQogNDk2IFs2OTkgMzg4IDY0MSA2MDUgNjEwIDYwMCA2MzggNTQzIDYxNiA2MzhdCiA2MDcgWzI1NyAyNzggMjU3XQogNjIxIFs1MTcgMCAwIDAgNDU5IDAgNTgyXQogNjMzIDYzNAo0MjQgNjc4IFsxMDU0IDcwOV0KIDczMCBbNTc2XQpdCi9EVyA2OTIKPj4K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DQowMDAwMDIwNTAxIDAwMDAwIG4NCjAwMDAwMjA3MDMgMDAwMDAgbg0KMDAwMDAyMDg5MyAwMDAwMCBuDQowMDAwMDIxMDY0IDAwMDAwIG4NCjAwMDAwMjEyMzggMDAwMDAgbg0KMDAwMDAyMTQ0NiAwMDAwMCBuDQowMDAwMDIxNjE1IDAwMDAwIG4NCjAwMDAwMjE3NjkgMDAwMDAgbg0KMDAwMDAyMTk1MyAwMDAwMCBuDQowMDAwMDIyMTIwIDAwMDAwIG4NCjAwMDAwMjIzMDEgMDAwMDAgbg0KMDAwMDAyMjQ0MCAwMDAwMCBuDQowMDAwMDIyNjMwIDAwMDAwIG4NCjAwMDAwMjI3ODkgMDAwMDAgbg0KMDAwMDAyMjg4MyAwMDAwMCBuDQowMDAwMDIyOTcxIDAwMDAwIG4NCjAwMDAwMjMwNjggMDAwMDAgbg0KMDAwMDAyMzQzOCAwMDAwMCBuDQowMDAwMDIzNTMzIDAwMDAwIG4NCjAwMDAwMjM2NDIgMDAwMDAgbg0KMDAwMDAyMzczMiAwMDAwMCBuDQowMDAwMDIzODM1IDAwMDAwIG4NCjAwMDAwMjM5MjIgMDAwMDAgbg0KMDAwMDAyNDAxMCAwMDAwMCBuDQowMDAwMDI0MTAzIDAwMDAwIG4NCjAwMDAwMjQxOTkgMDAwMDAgbg0KMDAwMDAyNDI4OCAwMDAwMCBuDQowMDAwMDI0Mzg2IDAwMDAwIG4NCjAwMDAwMjQ0ODUgMDAwMDAgbg0KMDAwMDAyNDU4NSAwMDAwMCBuDQowMDAwMDI0Njg1IDAwMDAwIG4NCjAwMDAwMjQ3ODMgMDAwMDAgbg0KMDAwMDAyNDg5NSAwMDAwMCBuDQowMDAwMDI1MDA0IDAwMDAwIG4NCjAwMDAwMjUxMTEgMDAwMDAgbg0KMDAwMDAyNTIwMCAwMDAwMCBuDQowMDAwMDI1Mjk1IDAwMDAwIG4NCjAwMDAwMjU0MTAgMDAwMDAgbg0KMDAwMDAyNTUzMiAwMDAwMCBuDQowMDAwMDI1NjQzIDAwMDAwIG4NCjAwMDAwMjU3NDIgMDAwMDAgbg0KMDAwMDAyNTg2OCAwMDAwMCBuDQowMDAwMDI1OTkzIDAwMDAwIG4NCjAwMDAwMjYwODggMDAwMDAgbg0KMDAwMDAyNjE4MyAwMDAwMCBuDQowMDAwMDI2Mjc4IDAwMDAwIG4NCjAwMDAwMjYzNzMgMDAwMDAgbg0KMDAwMDAyNjQ2OCAwMDAwMCBuDQowMDAwMDI2NTYzIDAwMDAwIG4NCjAwMDAwMjY2NTggMDAwMDAgbg0KMDAwMDAyNjc1MyAwMDAwMCBuDQowMDAwMDI2ODQ4IDAwMDAwIG4NCjAwMDAwMjY5NDMgMDAwMDAgbg0KMDAwMDAyNzAzOCAwMDAwMCBuDQowMDAwMDI3MDc4IDAwMDAwIG4NCjAwMDAwMjcxMjUgMDAwMDAgbg0KMDAwMDAyNzE3MCAwMDAwMCBuDQowMDAwMDI3NTAxIDAwMDAwIG4NCjAwMDAwMzI5NTEgMDAwMDAgbg0KMDAwMDAzMzQ0NiAwMDAwMCBuDQowMDAwMDMzNDkyIDAwMDAwIG4NCjAwMDAwMzM1NTIgMDAwMDAgbg0KMDAwMDAzMzY0OCAwMDAwMCBuDQowMDAwMDMzNzM2IDAwMDAwIG4NCjAwMDAwMzM4MjQgMDAwMDAgbg0KMDAwMDAzMzkxMiAwMDAwMCBuDQowMDAwMDM0MDAwIDAwMDAwIG4NCjAwMDAwMzQwODggMDAwMDAgbg0KMDAwMDAzNDE4NCAwMDAwMCBuDQowMDAwMDM0Mjg4IDAwMDAwIG4NCjAwMDAwMzQzODQgMDAwMDAgbg0KMDAwMDAzNDQ1NSAwMDAwMCBuDQowMDAwMDM0NTI2IDAwMDAwIG4NCjAwMDAwMzQ1OTcgMDAwMDAgbg0KMDAwMDAzNDY2OCAwMDAwMCBuDQowMDAwMDM0NzM5IDAwMDAwIG4NCjAwMDAwMzQ4MTAgMDAwMDAgbg0KMDAwMDAzNDg4MSAwMDAwMCBuDQowMDAwMDM0OTUyIDAwMDAwIG4NCjAwMDAwMzUwMjMgMDAwMDAgbg0KMDAwMDAzNTEyMCAwMDAwMCBuDQowMDAwMDM1MTkyIDAwMDAwIG4NCjAwMDAwMzUyNjQgMDAwMDAgbg0KMDAwMDAzNTMzNiAwMDAwMCBuDQowMDAwMDM1NDA4IDAwMDAwIG4NCjAwMDAwMzU0ODAgMDAwMDAgbg0KMDAwMDAzNTU1MiAwMDAwMCBuDQowMDAwMDM1NjI0IDAwMDAwIG4NCjAwMDAwMzU2OTYgMDAwMDAgbg0KMDAwMDAzNTc2OCAwMDAwMCBuDQowMDAwMDM1ODQwIDAwMDAwIG4NCjAwMDAwMzU5MTIgMDAwMDAgbg0KMDAwMDAzNTk4NCAwMDAwMCBuDQowMDAwMDM2MDU2IDAwMDAwIG4NCjAwMDAwMzYxMjggMDAwMDAgbg0KMDAwMDAzNjIyNiAwMDAwMCBuDQowMDAwMDM2MzIyIDAwMDAwIG4NCjAwMDAwMzY0MjEgMDAwMDAgbg0KMDAwMDAzNjUyMSAwMDAwMCBuDQowMDAwMDM2NjIxIDAwMDAwIG4NCjAwMDAwMzY3MjEgMDAwMDAgbg0KMDAwMDAzNjgyMCAwMDAwMCBuDQowMDAwMDM2OTE4IDAwMDAwIG4NCjAwMDAwMzcwMTUgMDAwMDAgbg0KMDAwMDAzNzExNSAwMDAwMCBuDQowMDAwMDM3MjE2IDAwMDAwIG4NCjAwMDAwMzcyOTYgMDAwMDAgbg0KMDAwMDAzNzMzMCAwMDAwMCBuDQowMDAwMDM3MzkxIDAwMDAwIG4NCjAwMDAwMzc3NjUgMDAwMDAgbg0KMDAwMDAzNzc5OSAwMDAwMCBuDQowMDAwMDM3ODM0IDAwMDAwIG4NCjAwMDAwMzc4OTUgMDAwMDAgbg0KMDAwMDAzODA0NiAwMDAwMCBuDQowMDAwMDM4MTk0IDAwMDAwIG4NCjAwMDAwMzgyNjQgMDAwMDAgbg0KMDAwMDAzODMzNCAwMDAwMCBuDQowMDAwMDM4NDA0IDAwMDAwIG4NCjAwMDAwMzg0NzQgMDAwMDAgbg0KMDAwMDAzODU0NCAwMDAwMCBuDQowMDAwMDM4NjE0IDAwMDAwIG4NCjAwMDAwMzg2ODQgMDAwMDAgbg0KMDAwMDAzODc1NCAwMDAwMCBuDQowMDAwMDM4ODI0IDAwMDAwIG4NCjAwMDAwMzg4OTUgMDAwMDAgbg0KMDAwMDAzODk2NiAwMDAwMCBuDQowMDAwMDM5MDM3IDAwMDAwIG4NCjAwMDAwMzkxMDggMDAwMDAgbg0KMDAwMDAzOTE3OSAwMDAwMCBuDQowMDAwMDM5MjUwIDAwMDAwIG4NCjAwMDAwMzkzMjEgMDAwMDAgbg0KMDAwMDAzOTM5MiAwMDAwMCBuDQowMDAwMDM5NDYzIDAwMDAwIG4NCjAwMDAwMzk1MzQgMDAwMDAgbg0KMDAwMDAzOTYwNSAwMDAwMCBuDQowMDAwMDM5Njc2IDAwMDAwIG4NCjAwMDAwMzk3NDcgMDAwMDAgbg0KMDAwMDAzOTgxOCAwMDAwMCBuDQowMDAwMDQwNTA3IDAwMDAwIG4NCjAwMDAwNDEwODIgMDAwMDAgbg0KMDAwMDA0MTQ0NiAwMDAwMCBuDQowMDAwMDQxODU1IDAwMDAwIG4NCjAwMDAwNDIwNTkgMDAwMDAgbg0KMDAwMDA0MjEzNSAwMDAwMCBuDQowMDAwMDQyMzM2IDAwMDAwIG4NCjAwMDAwNDI0MTIgMDAwMDAgbg0KMDAwMDA0NzI0MSAwMDAwMCBuDQp0cmFpbGVyCjw8Ci9Sb290IDEgMCBSCi9JbmZvIDkgMCBSCi9JRCBbPDM1QURCRjY1MTYyQjM5MEZFRkNCMzZDMDlFQTkxREZGOEYxRTMyNUMyNDMxNzE4NkVDMzIwQjQyQURERjQ0NEE+IDwzNUFEQkY2NTE2MkIzOTBGRUZDQjM2QzA5RUE5MURGRjhGMUUzMjVDMjQzMTcxODZFQzMyMEI0MkFEREY0NDRBPl0KL1NpemUgMTY3Cj4+CnN0YXJ0eHJlZgo0OTA5MQolJUVPRgo=" download="Jeeva_N_Resume.pdf" class="resume-download-btn" id="resumeBtn">
          <div class="resume-btn-inner">
            <div class="resume-btn-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="12" y1="18" x2="12" y2="12"/><polyline points="9 15 12 18 15 15"/></svg>
            </div>
            <div class="resume-btn-text">
              <span class="resume-btn-label">Resume</span>
              <span class="resume-btn-sub">Download PDF · 51KB</span>
            </div>
            <div class="resume-btn-arrow">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"/><polyline points="19 12 12 19 5 12"/></svg>
            </div>
          </div>
          <div class="resume-btn-progress"></div>
        </a>
      </div>
      <div class="sr">
        <div class="contact-links">
          <a href="tel:+917904145757" class="contact-link">
            <div class="link-icon">📞</div>
            <div class="link-meta"><div class="link-type">Phone</div><div class="link-val">+91 79041 45757</div></div>
            <span class="link-arrow">→</span>
          </a>
          <a href="mailto:nagarathinamjeeva7@gmail.com" class="contact-link">
            <div class="link-icon">✉️</div>
            <div class="link-meta"><div class="link-type">Email</div><div class="link-val">nagarathinamjeeva7@gmail.com</div></div>
            <span class="link-arrow">→</span>
          </a>
          <a href="https://www.linkedin.com/in/n-jeeva-5026bb295" target="_blank" class="contact-link">
            <div class="link-icon">💼</div>
            <div class="link-meta"><div class="link-type">LinkedIn</div><div class="link-val">n-jeeva-5026bb295</div></div>
            <span class="link-arrow">↗</span>
          </a>
          <div class="contact-link" style="cursor:default">
            <div class="link-icon">📍</div>
            <div class="link-meta"><div class="link-type">Location</div><div class="link-val">Paramakudi, Ramanathapuram, Tamil Nadu</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span>© 2026 Jeeva N</span>
  <span class="footer-status">System Online</span>
  <span>B.E. Electronics &amp; Communication Engineering</span>
</footer>

<script>
/* ─── CURSOR GLOW ─── */
const glow = document.getElementById('cursorGlow');
document.addEventListener('mousemove', e => {
  glow.style.left = e.clientX + 'px';
  glow.style.top = e.clientY + 'px';
});

/* ─── CANVAS PARTICLES ─── */
const canvas = document.getElementById('bg-canvas');
const ctx = canvas.getContext('2d');
let W, H, particles = [], nodes = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', () => { resize(); initParticles(); });

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.vx = (Math.random() - 0.5) * 0.4;
    this.vy = (Math.random() - 0.5) * 0.4;
    this.r = Math.random() * 1.5 + 0.5;
    this.alpha = Math.random() * 0.5 + 0.1;
    this.color = Math.random() > 0.6 ? '0,245,196' : Math.random() > 0.5 ? '0,201,255' : '168,85,247';
  }
  update() {
    this.x += this.vx; this.y += this.vy;
    if (this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
  }
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(${this.color},${this.alpha})`;
    ctx.fill();
  }
}

function initParticles() {
  particles = [];
  const count = Math.min(80, Math.floor(W * H / 12000));
  for (let i = 0; i < count; i++) particles.push(new Particle());
}
initParticles();

function drawConnections() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);
      if (dist < 120) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        const a = (1 - dist / 120) * 0.12;
        ctx.strokeStyle = `rgba(0,245,196,${a})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }
}

function animate() {
  ctx.clearRect(0, 0, W, H);
  drawConnections();
  particles.forEach(p => { p.update(); p.draw(); });
  requestAnimationFrame(animate);
}
animate();

/* ─── COUNTER ANIMATION ─── */
function animateCount(el) {
  const target = parseInt(el.dataset.count);
  const isDecimal = el.dataset.decimal;
  const dur = 1800;
  const start = performance.now();
  function step(now) {
    const t = Math.min((now - start) / dur, 1);
    const ease = 1 - Math.pow(1 - t, 3);
    const val = Math.round(target * ease);
    el.textContent = isDecimal ? (val / 100).toFixed(2) : val + (target === 3 ? 'x' : target === 4 ? '+' : '');
    if (t < 1) requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}

/* ─── SCROLL REVEAL ─── */
const srObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('vis');
      // Animate counters
      e.target.querySelectorAll('[data-count]').forEach(el => animateCount(el));
      // Animate skill bars
      e.target.querySelectorAll('.skill-fill[data-w]').forEach(bar => {
        bar.style.width = bar.dataset.w + '%';
      });
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('.sr,.sr-left,.exp-item').forEach(el => srObs.observe(el));

// Also trigger counters when hero stats come into view
document.querySelectorAll('.hero-stats .stat-num[data-count]').forEach(el => {
  setTimeout(() => animateCount(el), 1200);
});

// Skill bars in viewport on scroll
const skillObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.skill-fill[data-w]').forEach(bar => {
        bar.style.width = bar.dataset.w + '%';
      });
    }
  });
}, { threshold: 0.3 });
document.querySelectorAll('#skills').forEach(el => skillObs.observe(el));

/* ─── EXP ITEMS STAGGER ─── */
const expItems = document.querySelectorAll('.exp-item');
const expObs = new IntersectionObserver((entries) => {
  entries.forEach((e, i) => {
    if (e.isIntersecting) {
      setTimeout(() => e.target.classList.add('vis'), 100);
    }
  });
}, { threshold: 0.1 });
expItems.forEach((el, i) => {
  el.style.transitionDelay = (i * 120) + 'ms';
  expObs.observe(el);
});

/* ─── GLITCH EFFECT ─── */
const glitchEl = document.getElementById('glitch-name');
setInterval(() => {
  if (Math.random() > 0.92) {
    glitchEl.style.textShadow = '2px 0 #ff0080, -2px 0 #00f5c4';
    glitchEl.style.transform = `skewX(${(Math.random()-0.5)*4}deg)`;
    setTimeout(() => {
      glitchEl.style.textShadow = '';
      glitchEl.style.transform = '';
    }, 80);
  }
}, 300);

/* ─── ACTIVE NAV ─── */
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');
window.addEventListener('scroll', () => {
  let cur = '';
  sections.forEach(s => {
    if (window.scrollY >= s.offsetTop - 120) cur = s.id;
  });
  navLinks.forEach(a => {
    a.style.color = a.getAttribute('href') === '#' + cur ? 'var(--text)' : '';
  });
}, { passive: true });
</script>
</body>
</html>
