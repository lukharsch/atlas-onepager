<script setup>
import { onMounted } from 'vue'
import iconUrl from './assets/appicon.png'
import NavBar from './components/NavBar.vue'
import IPhoneMockup from './components/IPhoneMockup.vue'
import FeatureSection from './components/FeatureSection.vue'
import StatsCounter from './components/StatsCounter.vue'

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('revealed')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12, rootMargin: '0px 0px -40px 0px' }
  )
  document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el))
})
</script>

<template>
  <div>
    <NavBar />

    <!-- ── 1. Hero ─────────────────────────────────────────── -->
    <section class="hero" style="padding-left: 24px; padding-right: 24px;">
      <div class="blob blob-1" aria-hidden="true"></div>
      <div class="blob blob-2" aria-hidden="true"></div>
      <div class="blob blob-3" aria-hidden="true"></div>

      <div class="hero-content">
        <p class="section-eyebrow" data-reveal data-reveal-delay="1" style="margin-bottom:20px;">
          iOS App
        </p>

        <h1 class="hero-title" data-reveal data-reveal-delay="2">
          Every trip.<br>Beautifully<br>preserved.
        </h1>

        <p class="hero-sub" data-reveal data-reveal-delay="3">
          Atlas is a private travel journal that lives on your iPhone.
          Log trips, revisit memories, and explore your world — all encrypted, all yours.
        </p>

        <!--<div data-reveal data-reveal-delay="4" style="margin-bottom: 72px;">
          <a href="#" class="app-store-btn">
            <svg width="24" height="29" viewBox="0 0 24 29" fill="none" aria-hidden="true">
              <path d="M20.087 15.358c-.034-3.47 2.836-5.153 2.967-5.233-1.618-2.366-4.133-2.69-5.024-2.723-2.126-.217-4.172 1.265-5.252 1.265-1.098 0-2.77-1.24-4.565-1.205-2.33.035-4.498 1.369-5.698 3.452-2.44 4.232-.624 10.476 1.748 13.9 1.165 1.677 2.546 3.553 4.358 3.486 1.76-.072 2.42-1.127 4.545-1.127 2.107 0 2.72 1.127 4.566 1.088 1.89-.034 3.085-1.694 4.238-3.38 1.342-1.94 1.893-3.825 1.927-3.923-.043-.016-3.686-1.416-3.722-5.6z" fill="currentColor"/>
              <path d="M16.567 4.986c.966-1.172 1.62-2.8 1.44-4.42-1.393.056-3.08.929-4.08 2.1-.896 1.036-1.682 2.698-1.472 4.29 1.557.119 3.146-.79 4.112-1.97z" fill="currentColor"/>
            </svg>
            <span class="btn-label">
              <span class="btn-label-small">Download on the</span>
              <span class="btn-label-large">App Store</span>
            </span>
          </a>
        </div>-->

        <img class="app-store-btn" src="@/assets/download-app-store.svg"  alt=""/>

        <div class="hero-mockup" data-reveal data-reveal-delay="5">
          <IPhoneMockup label="Map View" color="dark" image-url="map" />
        </div>
      </div>
    </section>

    <!-- ── 2. Feature: Map ──────────────────────────────────── -->
    <!--<FeatureSection
      :dark="true"
      eyebrow="Map"
      title="Your world, pinned."
      body="Every trip you've ever taken, plotted on a living map. Realistic 3D terrain brings your adventures back to life at a glance."
      :bullets="[
        'Each trip drops a pin at your destination',
        'Tap any pin to preview details in a bottom sheet',
        'MapKit with realistic elevation and terrain',
      ]"
      mockup-label="Map View"
      mockup-color="dark"
      :reverse="false"
    />-->

    <!-- ── 3. Feature: Timeline ─────────────────────────────── -->
    <FeatureSection
      :dark="false"
      eyebrow="Timeline"
      title="Every adventure, in order."
      body="A chronological record of everywhere you've been. Browse by year, scan thumbnails, and jump straight into any memory."
      :bullets="[
        'Chronological list, grouped by year',
        'Trip thumbnails for instant recognition',
        'Tap any entry to open the full trip detail',
      ]"
      mockup-label="Timeline View"
      mockup-color="light"
      :reverse="true"
      image="timeline"
    />

    <!-- ── 4. Feature: Trip Detail ──────────────────────────── -->
    <FeatureSection
      :dark="true"
      eyebrow="Trip Detail"
      title="The full story of every trip."
      body="Hero photo, photo gallery, dates, and a mini map — everything about a journey, beautifully composed in one screen."
      :bullets="[
        'Full-bleed hero photo with gallery of up to 3 images',
        'Embedded mini map pinpointing your exact destination',
        'Location name, date range, and personal notes',
        'Swipe to move between photos seamlessly',
      ]"
      mockup-label="Trip Detail"
      mockup-color="dark"
      :reverse="false"
      image="tripdetail"
    />

    <!-- ── 5. Feature: Stats View ──────────────────────────── -->
    <FeatureSection
      :dark="false"
      eyebrow="Stats"
      title="See how far you've come."
      body="A personal dashboard that puts your entire travel history into perspective — countries mapped, cities discovered, and days spent exploring the world."
      :bullets="[
        'Countries visited, with an interactive breakdown',
        'Cities explored across every trip',
        'Total days spent travelling over your lifetime',
      ]"
      mockup-label="Stats View"
      mockup-color="light"
      :reverse="true"
      image="stats"
    />

    <!-- ── 7. Stats Strip ───────────────────────────────────── -->
    <section class="stats-section">
      <div data-reveal class="stats-eyebrow">
        <p class="section-eyebrow" style="margin-bottom:12px;">What a journey looks like</p>
        <p class="stats-sub">The kind of atlas you build over a lifetime.</p>
      </div>
      <div class="stats-grid">
        <StatsCounter :target="24" label="Countries" suffix="+" />
        <StatsCounter :target="67" label="Cities" />
        <StatsCounter :target="112" label="Trips" />
      </div>
    </section>

    <!-- ── 8. Encryption / Privacy ──────────────────────────── -->
    <section class="encryption-section">
      <div class="encryption-inner" data-reveal>
        <div class="lock-icon-wrap">
          <svg width="52" height="52" viewBox="0 0 52 52" fill="none" aria-hidden="true">
            <rect width="52" height="52" rx="15" fill="rgba(0,113,227,0.10)"/>
            <path d="M18 24v-4a8 8 0 0116 0v4" stroke="#0071e3" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
            <rect x="13" y="24" width="26" height="17" rx="4.5" fill="#0071e3" opacity="0.14"/>
            <rect x="13" y="24" width="26" height="17" rx="4.5" stroke="#0071e3" stroke-width="2.5"/>
            <circle cx="26" cy="33" r="2.5" fill="#0071e3"/>
            <line x1="26" y1="33" x2="26" y2="37" stroke="#0071e3" stroke-width="2.5" stroke-linecap="round"/>
          </svg>
        </div>

        <p class="section-eyebrow" style="margin-bottom:16px;">Privacy</p>

        <h2 class="encryption-title">Your memories, only yours.</h2>

        <p class="encryption-body">
          Every photo, every note, every location — encrypted with AES-GCM before it ever
          leaves the screen. Your key lives in the iOS Keychain, protected by Face ID or
          Touch ID. We have no server-side access to your data. Nobody does. Not even us.
        </p>

        <div class="encryption-tags">
          <span class="enc-tag">AES-GCM Encryption</span>
          <span class="enc-tag">iOS Keychain</span>
          <span class="enc-tag">Zero Server Access</span>
          <span class="enc-tag">Face ID &amp; Touch ID</span>
        </div>
      </div>
    </section>

    <!-- ── 9. Download CTA ──────────────────────────────────── -->
    <section class="cta-section">
      <div class="cta-blob cta-blob-1" aria-hidden="true"></div>
      <div class="cta-blob cta-blob-2" aria-hidden="true"></div>

      <div class="cta-content">
        <div data-reveal data-reveal-delay="1" style="margin-bottom:28px;">
          <img :src="iconUrl" alt="Atlas app icon" class="cta-icon" />
        </div>

        <p class="section-eyebrow" data-reveal data-reveal-delay="2" style="margin-bottom:20px;">
          Available now
        </p>
        <h2 class="cta-title" data-reveal data-reveal-delay="3">
          Start your atlas<br>today.
        </h2>
        <p class="cta-sub" data-reveal data-reveal-delay="4">
          Every trip is a story worth keeping. Atlas helps you keep them all.
        </p>
        <div data-reveal data-reveal-delay="5">
          <a href="#" class="app-store-btn">
            <svg width="24" height="29" viewBox="0 0 24 29" fill="none" aria-hidden="true">
              <path d="M20.087 15.358c-.034-3.47 2.836-5.153 2.967-5.233-1.618-2.366-4.133-2.69-5.024-2.723-2.126-.217-4.172 1.265-5.252 1.265-1.098 0-2.77-1.24-4.565-1.205-2.33.035-4.498 1.369-5.698 3.452-2.44 4.232-.624 10.476 1.748 13.9 1.165 1.677 2.546 3.553 4.358 3.486 1.76-.072 2.42-1.127 4.545-1.127 2.107 0 2.72 1.127 4.566 1.088 1.89-.034 3.085-1.694 4.238-3.38 1.342-1.94 1.893-3.825 1.927-3.923-.043-.016-3.686-1.416-3.722-5.6z" fill="currentColor"/>
              <path d="M16.567 4.986c.966-1.172 1.62-2.8 1.44-4.42-1.393.056-3.08.929-4.08 2.1-.896 1.036-1.682 2.698-1.472 4.29 1.557.119 3.146-.79 4.112-1.97z" fill="currentColor"/>
            </svg>
            <span class="btn-label">
              <span class="btn-label-small">Download on the</span>
              <span class="btn-label-large">App Store</span>
            </span>
          </a>
        </div>
      </div>
    </section>

    <!-- ── Footer ───────────────────────────────────────────── -->
    <footer class="site-footer">
      <div class="footer-inner">
        <span class="footer-wordmark">Atlas</span>
        <p class="footer-copy">
          &copy; {{ new Date().getFullYear() }} Atlas. Built for iOS.
        </p>
        <div class="footer-links">
          <a href="/privacy.html">Privacy Policy</a>
          <a href="mailto:lukas@lukasharsch.com">Support</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* ── Hero ─────────────────────────────────────────────────── */

.hero {
  position: relative;
  min-height: 100dvh;
  background: #0a0a0a;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
  padding: 0 0 clamp(80px, 10vw, 140px);
}

.blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
}
.blob-1 {
  width: 700px;
  height: 700px;
  background: radial-gradient(circle, rgba(0,113,227,0.20) 0%, transparent 70%);
  top: -220px;
  left: -120px;
}
.blob-2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(0,113,227,0.11) 0%, transparent 70%);
  top: 180px;
  right: -100px;
}
.blob-3 {
  width: 450px;
  height: 450px;
  background: radial-gradient(circle, rgba(100,60,255,0.09) 0%, transparent 70%);
  bottom: 60px;
  left: 32%;
}

.hero-content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding-top: clamp(120px, 16vh, 164px);
  width: 100%;
  max-width: 900px;
}

.hero-title {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(50px, 8.5vw, 100px);
  font-weight: 700;
  line-height: 1.04;
  letter-spacing: -0.04em;
  color: #ffffff;
  margin-bottom: 24px;
}

.hero-sub {
  font-size: clamp(16px, 2vw, 19px);
  line-height: 1.65;
  color: rgba(255, 255, 255, 0.52);
  max-width: 520px;
  margin-bottom: 40px;
}

.hero-mockup {
  margin-top: 8px;
}

/* ── Stats ────────────────────────────────────────────────── */

.stats-section {
  background: #080808;
  border-top: 1px solid rgba(255,255,255,0.06);
  border-bottom: 1px solid rgba(255,255,255,0.06);
  padding: clamp(72px, 10vw, 120px) clamp(24px, 5vw, 64px);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 64px;
}

.stats-eyebrow {
  text-align: center;
}

.stats-sub {
  font-size: 17px;
  color: rgba(255, 255, 255, 0.38);
  margin: 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: clamp(32px, 6vw, 80px);
  width: 100%;
  max-width: 900px;
  text-align: center;
}

@media (max-width: 560px) {
  .stats-grid { grid-template-columns: 1fr; gap: 52px; }
}

/* ── Encryption ──────────────────────────────────────────── */

.encryption-section {
  background: #ffffff;
  padding: clamp(80px, 12vw, 144px) clamp(24px, 5vw, 64px);
}

.encryption-inner {
  max-width: 680px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.lock-icon-wrap {
  margin-bottom: 28px;
}

.encryption-title {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(34px, 4.5vw, 54px);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.035em;
  color: #1d1d1f;
  margin-bottom: 22px;
}

.encryption-body {
  font-size: 17px;
  line-height: 1.72;
  color: rgba(29, 29, 31, 0.60);
  margin-bottom: 36px;
}

.encryption-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}

.enc-tag {
  font-size: 13px;
  font-weight: 500;
  padding: 8px 16px;
  border-radius: 999px;
  background: rgba(0, 113, 227, 0.07);
  color: #0071e3;
  border: 1px solid rgba(0, 113, 227, 0.18);
  letter-spacing: 0.01em;
}

/* ── CTA ──────────────────────────────────────────────────── */

.cta-section {
  position: relative;
  min-height: 70dvh;
  background: #0a0a0a;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  padding: 80px 24px;
  border-top: 1px solid rgba(255,255,255,0.06);
}

.cta-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
  pointer-events: none;
}
.cta-blob-1 {
  width: 650px;
  height: 650px;
  background: radial-gradient(circle, rgba(0,113,227,0.16) 0%, transparent 70%);
  bottom: -120px;
  right: -80px;
}
.cta-blob-2 {
  width: 420px;
  height: 420px;
  background: radial-gradient(circle, rgba(100,60,255,0.08) 0%, transparent 70%);
  top: -80px;
  left: 8%;
}

.cta-content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  max-width: 720px;
}

.cta-title {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(50px, 8vw, 92px);
  font-weight: 700;
  line-height: 1.06;
  letter-spacing: -0.04em;
  color: #ffffff;
  margin-bottom: 20px;
}

.cta-icon {
  width: 96px;
  height: 96px;
  border-radius: 22px;
  box-shadow: 0 24px 60px rgba(0, 0, 0, 0.55), 0 0 0 1px rgba(255, 255, 255, 0.10);
}

.cta-sub {
  font-size: clamp(16px, 1.8vw, 19px);
  color: rgba(255, 255, 255, 0.48);
  margin-bottom: 44px;
  line-height: 1.6;
  max-width: 440px;
}

/* ── Footer ──────────────────────────────────────────────── */

.site-footer {
  background: #0a0a0a;
  border-top: 1px solid rgba(255,255,255,0.07);
  padding: 40px 24px;
}

.footer-inner {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 16px;
}

.footer-wordmark {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: 16px;
  font-weight: 600;
  color: #ffffff;
  letter-spacing: -0.02em;
}

.footer-copy {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.28);
  margin: 0;
}

.footer-links {
  display: flex;
  gap: 24px;
}

.footer-links a {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.38);
  text-decoration: none;
  transition: color 0.2s;
}

.footer-links a:hover {
  color: rgba(255, 255, 255, 0.72);
}
</style>
