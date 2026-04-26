---
hide:
  - navigation
  - toc
---

<style>
/* ── HERO ───────────────────────────────────────────────── */
.hero-wrapper {
  position: relative;
  overflow: hidden;
  border-radius: 16px;
  margin: 2rem 0 3rem;
  padding: 5rem 2rem 4rem;
  background:
    radial-gradient(ellipse at 20% 50%, rgba(0, 200, 255, 0.12) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 30%, rgba(100, 60, 255, 0.15) 0%, transparent 60%),
    linear-gradient(135deg, #0d1117 0%, #161b22 50%, #0d1117 100%);
  text-align: center;
  box-shadow: 0 0 0 1px rgba(255,255,255,0.06), 0 24px 80px rgba(0,0,0,0.5);
}

/* Animated grid background */
.hero-wrapper::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(0,200,255,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,200,255,0.04) 1px, transparent 1px);
  background-size: 40px 40px;
  animation: gridPulse 8s ease-in-out infinite;
}

/* Glowing orb */
.hero-wrapper::after {
  content: '';
  position: absolute;
  top: -60px; left: 50%; transform: translateX(-50%);
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(0,200,255,0.08) 0%, transparent 70%);
  animation: orbPulse 4s ease-in-out infinite;
}

@keyframes gridPulse {
  0%, 100% { opacity: 0.5; }
  50%       { opacity: 1; }
}

@keyframes orbPulse {
  0%, 100% { transform: translateX(-50%) scale(1);   opacity: 0.6; }
  50%       { transform: translateX(-50%) scale(1.1); opacity: 1; }
}

.hero-badge {
  display: inline-block;
  background: rgba(0,200,255,0.1);
  border: 1px solid rgba(0,200,255,0.3);
  color: #00c8ff;
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  padding: 0.3rem 1rem;
  border-radius: 100px;
  margin-bottom: 1.5rem;
  position: relative; z-index: 1;
}

.hero-title {
  position: relative; z-index: 1;
  font-size: clamp(3rem, 8vw, 5.5rem);
  font-weight: 900;
  letter-spacing: -0.03em;
  line-height: 1;
  margin: 0 0 1rem;
  background: linear-gradient(135deg, #ffffff 0%, #00c8ff 50%, #7c3aed 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 6s ease-in-out infinite;
  background-size: 200% auto;
}

@keyframes shimmer {
  0%   { background-position: 0% center; }
  50%  { background-position: 100% center; }
  100% { background-position: 0% center; }
}

.hero-subtitle {
  position: relative; z-index: 1;
  font-size: 1.15rem;
  color: rgba(255,255,255,0.55);
  max-width: 520px;
  margin: 0 auto 2.5rem;
  line-height: 1.6;
  font-weight: 400;
}

.hero-subtitle strong {
  color: rgba(255,255,255,0.9);
}

.hero-buttons {
  position: relative; z-index: 1;
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: linear-gradient(135deg, #00c8ff, #7c3aed);
  color: #fff !important;
  text-decoration: none !important;
  padding: 0.8rem 2rem;
  border-radius: 10px;
  font-weight: 700;
  font-size: 0.95rem;
  letter-spacing: 0.01em;
  box-shadow: 0 4px 24px rgba(0,200,255,0.3), 0 0 0 1px rgba(255,255,255,0.1);
  transition: all 0.25s ease;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(0,200,255,0.45), 0 0 0 1px rgba(255,255,255,0.15);
}

.btn-secondary {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.12);
  color: rgba(255,255,255,0.8) !important;
  text-decoration: none !important;
  padding: 0.8rem 2rem;
  border-radius: 10px;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.25s ease;
}

.btn-secondary:hover {
  background: rgba(255,255,255,0.1);
  border-color: rgba(255,255,255,0.2);
  transform: translateY(-2px);
}

/* ── STATS BAR ──────────────────────────────────────────── */
.stats-bar {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin: 3rem 0 2rem;
}

.stat-chip {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 100px;
  padding: 0.35rem 1rem;
  font-size: 0.82rem;
  color: rgba(255,255,255,0.55);
  font-weight: 500;
}

.stat-chip span.dot {
  width: 7px; height: 7px;
  border-radius: 50%;
  background: #00c8ff;
  box-shadow: 0 0 6px #00c8ff;
  animation: blink 2s ease-in-out infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.3; }
}

/* ── SECTION LABEL ──────────────────────────────────────── */
.section-label {
  text-align: center;
  margin: 4rem 0 2rem;
}

.section-label h2 {
  font-size: 1.8rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: rgba(255,255,255,0.9);
  margin-bottom: 0.4rem;
}

.section-label p {
  color: rgba(255,255,255,0.4);
  font-size: 0.95rem;
}

/* ── FEATURE CARDS GRID ─────────────────────────────────── */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1rem;
  margin: 0 0 4rem;
}

.feature-card {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 12px;
  padding: 1.6rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.feature-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(0,200,255,0.4), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}

.feature-card:hover::before { opacity: 1; }
.feature-card:hover {
  border-color: rgba(0,200,255,0.2);
  background: rgba(0,200,255,0.04);
  transform: translateY(-3px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}

.feature-icon {
  font-size: 1.8rem;
  margin-bottom: 0.8rem;
  display: block;
}

.feature-card h3 {
  font-size: 1rem;
  font-weight: 700;
  color: rgba(255,255,255,0.9);
  margin: 0 0 0.5rem;
  letter-spacing: -0.01em;
}

.feature-card p {
  font-size: 0.875rem;
  color: rgba(255,255,255,0.45);
  margin: 0;
  line-height: 1.6;
}

/* ── FLOW DIAGRAM ───────────────────────────────────────── */
.flow-section {
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 16px;
  padding: 2.5rem 2rem;
  margin: 0 0 4rem;
}

.flow-steps {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0;
  flex-wrap: wrap;
}

.flow-step {
  text-align: center;
  padding: 1rem 1.5rem;
  flex: 1;
  min-width: 130px;
}

.flow-step .step-icon {
  width: 52px; height: 52px;
  border-radius: 12px;
  background: linear-gradient(135deg, rgba(0,200,255,0.15), rgba(124,58,237,0.15));
  border: 1px solid rgba(0,200,255,0.2);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.5rem;
  margin: 0 auto 0.7rem;
}

.flow-step h4 {
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.9);
  margin: 0 0 0.25rem;
}

.flow-step p {
  font-size: 0.78rem;
  color: rgba(255,255,255,0.4);
  margin: 0;
}

.flow-arrow {
  color: rgba(0,200,255,0.4);
  font-size: 1.2rem;
  flex-shrink: 0;
  padding: 0 0.2rem;
}

/* ── DOCS CTA ───────────────────────────────────────────── */
.docs-cta {
  background: linear-gradient(135deg,
    rgba(0,200,255,0.08) 0%,
    rgba(124,58,237,0.08) 100%
  );
  border: 1px solid rgba(0,200,255,0.15);
  border-radius: 16px;
  padding: 3rem 2rem;
  text-align: center;
  margin: 0 0 3rem;
}

.docs-cta h2 {
  font-size: 1.6rem;
  font-weight: 800;
  color: rgba(255,255,255,0.95);
  margin: 0 0 0.5rem;
  letter-spacing: -0.02em;
}

.docs-cta p {
  color: rgba(255,255,255,0.45);
  margin: 0 0 2rem;
}

/* ── TECH STACK PILLS ───────────────────────────────────── */
.tech-stack {
  display: flex;
  gap: 0.6rem;
  justify-content: center;
  flex-wrap: wrap;
  margin: 2rem 0;
}

.tech-pill {
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 8px;
  padding: 0.45rem 1rem;
  font-size: 0.82rem;
  font-weight: 600;
  color: rgba(255,255,255,0.6);
  letter-spacing: 0.02em;
}

.tech-pill.highlight {
  background: rgba(0,200,255,0.08);
  border-color: rgba(0,200,255,0.25);
  color: #00c8ff;
}
</style>

<!-- ╔══════════════════════════════════════╗ -->
<!-- ║            HERO SECTION             ║ -->
<!-- ╚══════════════════════════════════════╝ -->

<div class="hero-wrapper">
  <div class="hero-badge">⚡ Made by methano_</div>
  <h1 class="hero-title"><strong>DealerBot</strong></h1>
  <p class="hero-subtitle">
    Sistema intelligente di distribuzione carte via <strong>infrarossi</strong>.<br>
    ATtiny85 · Protocollo NEC · Arduino IDE
  </p>
  <div class="hero-buttons">
    <a href="telecomandi/" class="btn-primary">Documentazione Telecomandi</a>
    <a href="#come-funziona" class="btn-secondary">↓ Come funziona</a>
  </div>
</div>

<!-- ── STATUS CHIPS ── -->
<div class="stats-bar">
  <div class="stat-chip"><span class="dot"></span> Protocollo NEC 38kHz</div>
  <div class="stat-chip">ATtiny85 @ 8 MHz</div>
  <div class="stat-chip">Libreria IRremote v4.x</div>
  <div class="stat-chip">Programmato via Arduino ISP</div>
</div>

---

<!-- ╔══════════════════════════════════════╗ -->
<!-- ║         FEATURE CARDS               ║ -->
<!-- ╚══════════════════════════════════════╝ -->

<div class="section-label" id="come-funziona">
  <h2>Come funziona</h2>
  <p>Un sistema completo da zero componenti a distribuzione automatica</p>
</div>

<div class="features-grid">
  <div class="feature-card">
    <span class="feature-icon">📡</span>
    <h3>Trasmissione IR</h3>
    <p>Ogni telecomando ATtiny85 emette un codice NEC univoco a 38 kHz quando si preme il pulsante.</p>
  </div>
  <div class="feature-card">
    <span class="feature-icon">🔍</span>
    <h3>Riconoscimento Giocatore</h3>
    <p>Il ricevitore centrale decodifica il segnale e identifica quale giocatore ha inviato la richiesta.</p>
  </div>
  <div class="feature-card">
    <span class="feature-icon">🃏</span>
    <h3>Distribuzione Automatica</h3>
    <p>La logica centrale assegna la carta corretta al giocatore in base al codice ricevuto.</p>
  </div>
  <div class="feature-card">
    <span class="feature-icon">⚙️</span>
    <h3>Firmware Custom</h3>
    <p>Ogni ATtiny85 è programmato via Arduino ISP con un codice esadecimale diverso per ogni telecomando.</p>
  </div>
</div>

---

<!-- ╔══════════════════════════════════════╗ -->
<!-- ║           FLUSSO OPERATIVO          ║ -->
<!-- ╚══════════════════════════════════════╝ -->

<div class="section-label">
  <h2>Flusso Operativo</h2>
  <p>Dal pulsante alla carta — 4 passaggi</p>
</div>

<div class="flow-section">
  <div class="flow-steps">
    <div class="flow-step">
      <div class="step-icon">👆</div>
      <h4>Pressione</h4>
      <p>Il giocatore preme il tasto sul telecomando</p>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-step">
      <div class="step-icon">📤</div>
      <h4>Trasmissione</h4>
      <p>ATtiny85 invia il codice IR univoco via LED</p>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-step">
      <div class="step-icon">📥</div>
      <h4>Decodifica</h4>
      <p>Il ricevitore centrale interpreta il protocollo NEC</p>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-step">
      <div class="step-icon">🃏</div>
      <h4>Assegnazione</h4>
      <p>La carta viene distribuita al giocatore corretto</p>
    </div>
  </div>
</div>

---

<!-- ╔══════════════════════════════════════╗ -->
<!-- ║              DOCS CTA               ║ -->
<!-- ╚══════════════════════════════════════╝ -->

<div class="docs-cta">
  <h2>Pronto ad iniziare?</h2>
  <p>Consulta la documentazione completa dei telecomandi per setup, firmware e debug</p>
  <a href="telecomandi/" class="btn-primary">Apri la Documentazione Completa</a>
</div>
