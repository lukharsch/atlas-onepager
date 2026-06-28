<script setup>
import iconUrl from './assets/appicon.png'

const lastUpdated = 'June 28, 2026'
</script>

<template>
  <div class="page">

    <!-- Nav -->
    <nav class="pp-nav">
      <div class="pp-nav-inner">
        <a href="/" class="pp-wordmark">
          <img :src="iconUrl" alt="Atlas" class="pp-icon" />
          <span>Atlas</span>
        </a>
        <a href="/" class="pp-back">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <path d="M10 3L5 8l5 5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Back
        </a>
      </div>
    </nav>

    <!-- Content -->
    <main class="pp-main">
      <div class="pp-container">

        <header class="pp-header">
          <p class="pp-eyebrow">Legal</p>
          <h1 class="pp-title">Privacy Policy</h1>
          <p class="pp-meta">Last updated: {{ lastUpdated }}</p>
          <p class="pp-intro">
            Atlas is built on the belief that your travel memories belong to you — and only you.
            This policy explains in plain language how Atlas handles your data, what we store,
            what we cannot access, and what you should know before relying on the app.
            Please read it carefully.
          </p>
        </header>

        <div class="pp-body">

          <!-- 1. Encryption & iOS Keychain -->
          <section class="pp-section">
            <h2>Encryption &amp; the iOS Keychain</h2>
            <p>
              All data you create in Atlas (except trip dates) — meaning trip titles, locations, notes, and photos —
              is encrypted on your device using AES-GCM before it is written to storage.
              The encryption key is generated locally and stored exclusively in the
              <strong>iOS Keychain</strong>, Apple's secure credential store. Atlas never
              transmits your encryption key or your unencrypted data to any server.
            </p>
            <p>
              Because the key lives only in your device's Keychain, <strong>what happens
              to that key is entirely determined by your iCloud Keychain settings</strong>:
            </p>
            <ul>
              <li>
                <strong>iCloud Keychain enabled:</strong> Apple may sync the key to your other
                trusted Apple devices, which would allow Atlas to decrypt and display your data
                on those devices. This sync is controlled by Apple and governed by Apple's
                own privacy policy, not ours.
              </li>
              <li>
                <strong>iCloud Keychain disabled:</strong> The encryption key exists only on the
                single physical device where Atlas is installed. It will not transfer to any
                other device.
              </li>
            </ul>
            <div class="pp-callout pp-callout-warning">
              <strong>Important — data loss risk when changing devices:</strong> If you
              restore to a new iPhone, perform a factory reset, or use a device that does
              not have access to the original Keychain entry (e.g. iCloud Keychain is off,
              you are signing into a different Apple ID, or the Keychain entry was otherwise
              deleted), <strong>your Atlas data cannot be recovered</strong>. There is no
              server-side backup, no recovery key, and no support process that can restore
              encrypted data once the key is gone. This is a deliberate privacy trade-off.
            </div>
            <p>
              We strongly recommend enabling iCloud Keychain if you wish to preserve
              access to your data across devices or after a device replacement.
            </p>
          </section>

          <!-- 2. Photo Compression -->
          <section class="pp-section">
            <h2>Photo Compression</h2>
            <p>
              When you add photos to a trip, Atlas compresses them on-device before
              encrypting and storing them. This reduces storage consumption and keeps the
              app performant across all supported devices.
            </p>
            <p>
              As a result, <strong>photos stored in Atlas will not retain their original
              full resolution or file size</strong>. While we aim for a compression level
              that keeps images visually pleasing and suitable for on-screen viewing, we make
              no guarantee regarding the preservation of original image quality, metadata
              (such as EXIF data), or color fidelity. Atlas is not intended as a replacement
              for your camera roll or a professional photo archive.
            </p>
          </section>

          <!-- 3. Data Availability -->
          <section class="pp-section">
            <h2>No Guarantee of Data Availability</h2>
            <p>
              Atlas stores your data locally on your device. We do not operate a cloud backup
              service or any infrastructure that retains copies of your trips, photos, or
              account information.
            </p>
            <p>
              <strong>We make no guarantee that your data will be available, intact, or
              accessible at any given time.</strong> Data may become inaccessible or lost due
              to — but not limited to — device failure, iOS updates, app corruption, deletion
              of the app, loss of the Keychain entry, or any other circumstance beyond our
              control. You are solely responsible for maintaining any backups of your data
              through means outside of Atlas (such as exporting photos to your camera roll
              before adding them to the app).
            </p>
          </section>

          <!-- 4. Service Discontinuation -->
          <section class="pp-section">
            <h2>Service Discontinuation</h2>
            <p>
              Atlas is provided as-is and at our sole discretion. <strong>We reserve the
              right to discontinue, suspend, or significantly alter the application at any
              time, for any reason, without prior notice or communication.</strong> This
              includes but is not limited to removing the app from the App Store, releasing
              updates that change existing functionality, or ceasing development entirely.
            </p>
            <p>
              In the event of discontinuation, no refund or compensation will be offered for
              any interruption of service. Because your data is stored locally and encrypted
              on your device, the availability of Atlas as a running application does not
              affect your ability to access data through other means, though we cannot
              guarantee that either.
            </p>
          </section>

          <!-- 5. Free App / No Warranty -->
          <section class="pp-section">
            <h2>Free to Use — No Warranty</h2>
            <p>
              Atlas is currently provided free of charge. We reserve the right to introduce
              paid features, subscriptions, or pricing changes in the future, with or without
              advance notice.
            </p>
            <p>
              <strong>Because Atlas is provided free of charge, it is provided entirely
              without warranty of any kind</strong>, express or implied. This includes,
              without limitation, any implied warranties of merchantability, fitness for a
              particular purpose, accuracy, reliability, or non-infringement. Your use of
              Atlas is entirely at your own risk. We shall not be liable for any loss of
              data, device damage, or any other direct, indirect, incidental, or
              consequential damages arising from your use of the app.
            </p>
          </section>

          <!-- 6. Data We Do Not Collect -->
          <section class="pp-section">
            <h2>Data We Do Not Collect</h2>
            <p>
              Atlas does not collect, transmit, or have access to your personal data,
              trip content, photos, or location history. We do not operate analytics
              pipelines, advertising networks, or user tracking of any kind within the app.
              We do not receive crash reports containing personal data unless you explicitly
              choose to share diagnostics with Apple through iOS settings.
            </p>
          </section>

          <!-- 7. Changes to This Policy -->
          <section class="pp-section">
            <h2>Changes to This Policy</h2>
            <p>
              We may update this Privacy Policy from time to time. When we do, the
              "Last updated" date at the top of this page will change. Continued use of
              Atlas after any change constitutes your acceptance of the revised policy.
              We encourage you to review this page periodically.
            </p>
          </section>

          <!-- 8. Contact -->
          <section class="pp-section pp-section-last">
            <h2>Contact</h2>
            <p>
              If you have questions about this Privacy Policy or Atlas in general,
              you can reach us at:
            </p>
            <a href="mailto:lukas@lukasharsch.com" class="pp-contact-link">
              lukas@lukasharsch.com
            </a>
          </section>

        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer class="pp-footer">
      <div class="pp-footer-inner">
        <span class="pp-footer-wordmark">Atlas</span>
        <p class="pp-footer-copy">
          &copy; {{ new Date().getFullYear() }} Atlas. Built for iOS.
        </p>
        <a href="/" class="pp-footer-back">Back to home</a>
      </div>
    </footer>

  </div>
</template>

<style scoped>
.page {
  min-height: 100dvh;
  background: #ffffff;
  display: flex;
  flex-direction: column;
}

/* ── Nav ──────────────────────────────────────────────────── */

.pp-nav {
  background: #0a0a0a;
  border-bottom: 1px solid rgba(255, 255, 255, 0.07);
  position: sticky;
  top: 0;
  z-index: 50;
}

.pp-nav-inner {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 24px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.pp-wordmark {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  color: #ffffff;
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: 18px;
  font-weight: 600;
  letter-spacing: -0.025em;
}

.pp-icon {
  width: 28px;
  height: 28px;
  border-radius: 7px;
}

.pp-back {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  color: rgba(255, 255, 255, 0.5);
  text-decoration: none;
  font-size: 14px;
  transition: color 0.2s;
}

.pp-back:hover {
  color: #ffffff;
}

/* ── Main ─────────────────────────────────────────────────── */

.pp-main {
  flex: 1;
  padding: clamp(48px, 8vw, 96px) 24px;
}

.pp-container {
  max-width: 720px;
  margin: 0 auto;
}

/* ── Header ───────────────────────────────────────────────── */

.pp-eyebrow {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #0071e3;
  margin: 0 0 14px;
}

.pp-title {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(38px, 5vw, 56px);
  font-weight: 700;
  line-height: 1.08;
  letter-spacing: -0.035em;
  color: #1d1d1f;
  margin: 0 0 12px;
}

.pp-meta {
  font-size: 13px;
  color: rgba(29, 29, 31, 0.4);
  margin: 0 0 32px;
}

.pp-intro {
  font-size: 17px;
  line-height: 1.7;
  color: rgba(29, 29, 31, 0.65);
  padding-bottom: 48px;
  border-bottom: 1px solid rgba(29, 29, 31, 0.10);
  margin: 0;
}

/* ── Sections ─────────────────────────────────────────────── */

.pp-body {
  padding-top: 8px;
}

.pp-section {
  padding: 44px 0;
  border-bottom: 1px solid rgba(29, 29, 31, 0.08);
}

.pp-section-last {
  border-bottom: none;
}

.pp-section h2 {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: 22px;
  font-weight: 650;
  letter-spacing: -0.02em;
  color: #1d1d1f;
  margin: 0 0 16px;
}

.pp-section p {
  font-size: 16px;
  line-height: 1.72;
  color: rgba(29, 29, 31, 0.70);
  margin: 0 0 16px;
}

.pp-section p:last-child {
  margin-bottom: 0;
}

.pp-section ul {
  margin: 0 0 16px;
  padding: 0 0 0 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.pp-section li {
  font-size: 16px;
  line-height: 1.65;
  color: rgba(29, 29, 31, 0.70);
  padding-left: 4px;
}

.pp-section strong {
  font-weight: 600;
  color: #1d1d1f;
}

/* ── Warning callout ──────────────────────────────────────── */

.pp-callout {
  border-radius: 14px;
  padding: 20px 24px;
  margin: 24px 0;
  font-size: 15px;
  line-height: 1.65;
}

.pp-callout-warning {
  background: rgba(255, 149, 0, 0.08);
  border: 1px solid rgba(255, 149, 0, 0.22);
  color: rgba(29, 29, 31, 0.80);
}

.pp-callout-warning strong {
  color: #b05f00;
  font-weight: 600;
}

/* ── Contact ──────────────────────────────────────────────── */

.pp-contact-link {
  display: inline-block;
  margin-top: 8px;
  font-size: 16px;
  font-weight: 500;
  color: #0071e3;
  text-decoration: none;
  border-bottom: 1px solid rgba(0, 113, 227, 0.25);
  padding-bottom: 2px;
  transition: border-color 0.2s;
}

.pp-contact-link:hover {
  border-color: #0071e3;
}

/* ── Footer ───────────────────────────────────────────────── */

.pp-footer {
  background: #0a0a0a;
  border-top: 1px solid rgba(255, 255, 255, 0.07);
  padding: 32px 24px;
}

.pp-footer-inner {
  max-width: 720px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
}

.pp-footer-wordmark {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: 15px;
  font-weight: 600;
  color: #ffffff;
  letter-spacing: -0.02em;
}

.pp-footer-copy {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.28);
  margin: 0;
}

.pp-footer-back {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.38);
  text-decoration: none;
  transition: color 0.2s;
}

.pp-footer-back:hover {
  color: rgba(255, 255, 255, 0.75);
}
</style>
