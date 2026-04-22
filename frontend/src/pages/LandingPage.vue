<template>
  <div class="landing">

    <!-- Navbar -->
    <header class="nav">
      <div class="nav-logo">📍 EventLocal</div>
      <nav class="nav-links">
        <a href="#">Features</a>
        <a href="#">Events</a>
        <a href="#">Pricing</a>
        <a href="#">About</a>
      </nav>
      <div class="nav-actions">
        <router-link to="/login" class="btn-ghost-sm">Log in</router-link>
        <router-link to="/register" class="btn-primary-sm">Get Started</router-link>
      </div>
    </header>

    <!-- Hero -->
    <section class="hero">
      <div class="hero-badge">✨ The #1 Event Platform</div>
      <h1 class="hero-title">Create & Manage<br /><span class="gradient-text">Unforgettable Events</span></h1>
      <p class="hero-sub">Plan, promote, and sell tickets for any event — from intimate gatherings to massive festivals. All in one place.</p>
      <div class="hero-cta">
        <router-link to="/register" class="btn-hero">Start for Free</router-link>
        <router-link to="/events" class="btn-hero-ghost">Browse Events →</router-link>
      </div>
      <div class="hero-stats">
        <div class="stat"><span class="stat-num">50K+</span><span class="stat-label">Events Created</span></div>
        <div class="stat-divider"></div>
        <div class="stat"><span class="stat-num">2M+</span><span class="stat-label">Tickets Sold</span></div>
        <div class="stat-divider"></div>
        <div class="stat"><span class="stat-num">120+</span><span class="stat-label">Countries</span></div>
      </div>
    </section>

    <!-- Event Preview Cards -->
    <section class="preview-section">
      <h2 class="section-title">Trending Near You</h2>
      <div class="cards-row">
        <div v-for="e in sampleEvents" :key="e.id" class="preview-card">
          <div class="preview-img" :style="{ background: e.color }">
            <span class="preview-emoji">{{ e.emoji }}</span>
            <span class="preview-badge">{{ e.category }}</span>
          </div>
          <div class="preview-body">
            <div class="preview-date">{{ e.date }}</div>
            <div class="preview-title">{{ e.title }}</div>
            <div class="preview-loc">📍 {{ e.location }}</div>
            <div class="preview-footer">
              <span class="preview-price">{{ e.price }}</span>
              <button class="btn-card">RSVP</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Features -->
    <section class="features-section">
      <h2 class="section-title">Everything You Need</h2>
      <div class="features-grid">
        <div v-for="f in features" :key="f.title" class="feature-card">
          <div class="feature-icon">{{ f.icon }}</div>
          <h3>{{ f.title }}</h3>
          <p>{{ f.desc }}</p>
        </div>
      </div>
    </section>

    <!-- CTA Banner -->
    <section class="cta-section">
      <h2>Ready to host your next event?</h2>
      <p>Join thousands of organizers who trust EventLocal.</p>
      <router-link to="/register" class="btn-hero">Create Your Event →</router-link>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <span>📍 EventLocal © 2025</span>
      <div class="footer-links">
        <a href="#">Privacy</a>
        <a href="#">Terms</a>
        <a href="#">Contact</a>
      </div>
    </footer>

  </div>
</template>

<script setup>
const sampleEvents = [
  { id: 1, title: 'Summer Music Festival', category: 'Music', date: 'Sat, Jul 12', location: 'Central Park, NY', price: '$25', emoji: '🎵', color: 'linear-gradient(135deg,#667eea,#764ba2)' },
  { id: 2, title: 'Tech Summit 2025', category: 'Tech', date: 'Fri, Aug 1', location: 'San Francisco, CA', price: 'Free', emoji: '💻', color: 'linear-gradient(135deg,#f093fb,#f5576c)' },
  { id: 3, title: 'Food & Wine Expo', category: 'Food', date: 'Sun, Jul 20', location: 'Chicago, IL', price: '$15', emoji: '🍷', color: 'linear-gradient(135deg,#4facfe,#00f2fe)' },
  { id: 4, title: 'City Marathon 2025', category: 'Sports', date: 'Sat, Sep 6', location: 'Boston, MA', price: '$30', emoji: '🏃', color: 'linear-gradient(135deg,#43e97b,#38f9d7)' },
]

const features = [
  { icon: '🎟️', title: 'Easy Ticketing', desc: 'Sell tickets online with zero setup. Support for free, paid, and tiered pricing.' },
  { icon: '📊', title: 'Live Analytics', desc: 'Track registrations, revenue, and attendance in real time from your dashboard.' },
  { icon: '📣', title: 'Promotion Tools', desc: 'Share events across social media and email with one click.' },
  { icon: '🗺️', title: 'Venue Maps', desc: 'Interactive seating charts and venue maps for any event size.' },
  { icon: '🤝', title: 'Team Collaboration', desc: 'Invite co-organizers and manage roles with granular permissions.' },
  { icon: '🔒', title: 'Secure Payments', desc: 'PCI-compliant payments with instant payouts to your account.' },
]
</script>

<style scoped>
.landing {
  min-height: 100vh;
  background: #0a0a0f;
  color: #fff;
  font-family: 'Inter', sans-serif;
}

/* Nav */
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 60px;
  border-bottom: 1px solid rgba(255,255,255,0.08);
  position: sticky;
  top: 0;
  background: rgba(10,10,15,0.9);
  backdrop-filter: blur(12px);
  z-index: 100;
}
.nav-logo { font-size: 20px; font-weight: 700; color: #a78bfa; }
.nav-links { display: flex; gap: 32px; }
.nav-links a { font-size: 14px; color: rgba(255,255,255,0.6); transition: color 0.2s; }
.nav-links a:hover { color: #fff; }
.nav-actions { display: flex; gap: 12px; align-items: center; }
.btn-ghost-sm { font-size: 14px; color: rgba(255,255,255,0.7); padding: 8px 16px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.15); transition: all 0.2s; }
.btn-ghost-sm:hover { background: rgba(255,255,255,0.08); color: #fff; }
.btn-primary-sm { font-size: 14px; font-weight: 600; color: #0a0a0f; background: #a78bfa; padding: 8px 18px; border-radius: 8px; transition: background 0.2s; }
.btn-primary-sm:hover { background: #c4b5fd; }

/* Hero */
.hero {
  text-align: center;
  padding: 100px 24px 80px;
  max-width: 800px;
  margin: 0 auto;
}
.hero-badge {
  display: inline-block;
  background: rgba(167,139,250,0.15);
  border: 1px solid rgba(167,139,250,0.3);
  color: #c4b5fd;
  font-size: 13px;
  font-weight: 600;
  padding: 6px 16px;
  border-radius: 999px;
  margin-bottom: 28px;
}
.hero-title {
  font-size: clamp(40px, 6vw, 72px);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 20px;
  letter-spacing: -1px;
}
.gradient-text {
  background: linear-gradient(135deg, #a78bfa, #f472b6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-sub { font-size: 18px; color: rgba(255,255,255,0.55); line-height: 1.7; margin-bottom: 40px; }
.hero-cta { display: flex; gap: 16px; justify-content: center; flex-wrap: wrap; margin-bottom: 60px; }
.btn-hero {
  background: linear-gradient(135deg, #a78bfa, #f472b6);
  color: #fff;
  font-weight: 700;
  font-size: 16px;
  padding: 14px 32px;
  border-radius: 12px;
  transition: opacity 0.2s;
}
.btn-hero:hover { opacity: 0.88; }
.btn-hero-ghost {
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.15);
  color: rgba(255,255,255,0.8);
  font-size: 16px;
  font-weight: 600;
  padding: 14px 32px;
  border-radius: 12px;
  transition: all 0.2s;
}
.btn-hero-ghost:hover { background: rgba(255,255,255,0.12); color: #fff; }
.hero-stats { display: flex; align-items: center; justify-content: center; gap: 32px; }
.stat { display: flex; flex-direction: column; align-items: center; gap: 4px; }
.stat-num { font-size: 28px; font-weight: 800; color: #fff; }
.stat-label { font-size: 12px; color: rgba(255,255,255,0.45); text-transform: uppercase; letter-spacing: 0.5px; }
.stat-divider { width: 1px; height: 40px; background: rgba(255,255,255,0.12); }

/* Preview Cards */
.preview-section { padding: 60px 60px; }
.section-title { font-size: 28px; font-weight: 700; margin-bottom: 32px; text-align: center; }
.cards-row { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 20px; }
.preview-card {
  background: #13131a;
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 16px;
  overflow: hidden;
  transition: transform 0.2s, border-color 0.2s;
}
.preview-card:hover { transform: translateY(-4px); border-color: rgba(167,139,250,0.4); }
.preview-img {
  height: 140px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
.preview-emoji { font-size: 48px; }
.preview-badge {
  position: absolute;
  top: 10px;
  left: 10px;
  background: rgba(0,0,0,0.45);
  backdrop-filter: blur(6px);
  color: #fff;
  font-size: 11px;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 999px;
}
.preview-body { padding: 14px; display: flex; flex-direction: column; gap: 6px; }
.preview-date { font-size: 12px; color: #a78bfa; font-weight: 600; }
.preview-title { font-size: 15px; font-weight: 700; }
.preview-loc { font-size: 12px; color: rgba(255,255,255,0.45); }
.preview-footer { display: flex; align-items: center; justify-content: space-between; margin-top: 6px; }
.preview-price { font-size: 14px; font-weight: 700; color: #4ade80; }
.btn-card {
  background: rgba(167,139,250,0.15);
  color: #a78bfa;
  font-size: 12px;
  font-weight: 700;
  padding: 6px 14px;
  border-radius: 8px;
  border: 1px solid rgba(167,139,250,0.3);
  transition: all 0.2s;
}
.btn-card:hover { background: #a78bfa; color: #fff; }

/* Features */
.features-section { padding: 60px 60px; background: #0d0d14; }
.features-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 20px; }
.feature-card {
  background: #13131a;
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 16px;
  padding: 28px;
  transition: border-color 0.2s;
}
.feature-card:hover { border-color: rgba(167,139,250,0.35); }
.feature-icon { font-size: 32px; margin-bottom: 14px; }
.feature-card h3 { font-size: 16px; font-weight: 700; margin-bottom: 8px; }
.feature-card p { font-size: 13px; color: rgba(255,255,255,0.5); line-height: 1.6; }

/* CTA */
.cta-section {
  text-align: center;
  padding: 80px 24px;
  background: linear-gradient(135deg, rgba(167,139,250,0.12), rgba(244,114,182,0.12));
  border-top: 1px solid rgba(255,255,255,0.06);
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.cta-section h2 { font-size: 36px; font-weight: 800; margin-bottom: 12px; }
.cta-section p { font-size: 16px; color: rgba(255,255,255,0.5); margin-bottom: 32px; }

/* Footer */
.footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px 60px;
  font-size: 13px;
  color: rgba(255,255,255,0.35);
}
.footer-links { display: flex; gap: 24px; }
.footer-links a { color: rgba(255,255,255,0.35); transition: color 0.2s; }
.footer-links a:hover { color: #fff; }

@media (max-width: 768px) {
  .nav { padding: 16px 20px; }
  .nav-links { display: none; }
  .preview-section, .features-section { padding: 40px 20px; }
  .footer { padding: 20px; flex-direction: column; gap: 12px; }
}
</style>
