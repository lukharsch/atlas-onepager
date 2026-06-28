<script setup>
import IPhoneMockup from './IPhoneMockup.vue'

defineProps({
  dark: { type: Boolean, default: true },
  eyebrow: { type: String, default: '' },
  title: { type: String, required: true },
  body: { type: String, default: '' },
  bullets: { type: Array, default: () => [] },
  mockupLabel: { type: String, required: true },
  mockupColor: { type: String, default: 'dark' },
  reverse: { type: Boolean, default: false },
  image: { type: String, default: '' }
})
</script>

<template>
  <section
    class="feature-section"
    :style="dark
      ? 'background:#0a0a0a; border-top: 1px solid rgba(255,255,255,0.06);'
      : 'background:#ffffff;'"
  >
    <div
      class="feature-inner"
      :class="reverse ? 'reverse' : ''"
    >
      <!-- Phone mockup -->
      <div
        class="mockup-col"
        :data-reveal="reverse ? 'from-right' : 'from-left'"
      >
        <IPhoneMockup :label="mockupLabel" :color="mockupColor" :imageUrl="image" />
      </div>

      <!-- Text content -->
      <div class="text-col" data-reveal>
        <p v-if="eyebrow" class="section-eyebrow" style="margin-bottom: 16px;">{{ eyebrow }}</p>

        <h2
          class="feature-title"
          :style="dark ? 'color:#ffffff;' : 'color:#1d1d1f;'"
        >
          {{ title }}
        </h2>

        <p
          v-if="body"
          class="feature-body"
          :style="dark ? 'color:rgba(255,255,255,0.6);' : 'color:rgba(29,29,31,0.65);'"
        >
          {{ body }}
        </p>

        <ul v-if="bullets.length" class="bullet-list">
          <li
            v-for="(bullet, i) in bullets"
            :key="i"
            class="bullet-item"
            :style="dark ? 'color:rgba(255,255,255,0.72);' : 'color:rgba(29,29,31,0.75);'"
          >
            <span
              class="bullet-dot"
              :style="dark ? 'background: rgba(255,255,255,0.15);' : 'background: rgba(29,29,31,0.12);'"
            ></span>
            {{ bullet }}
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.feature-section {
  padding: clamp(80px, 10vw, 140px) clamp(24px, 5vw, 64px);
}

.feature-inner {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: clamp(48px, 7vw, 96px);
}

.feature-inner.reverse {
  direction: rtl;
}
.feature-inner.reverse > * {
  direction: ltr;
}

.mockup-col {
  display: flex;
  justify-content: center;
}

.text-col {
  display: flex;
  flex-direction: column;
}

.feature-title {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(34px, 4.5vw, 56px);
  font-weight: 700;
  line-height: 1.08;
  letter-spacing: -0.035em;
  margin-bottom: 20px;
}

.feature-body {
  font-size: 17px;
  line-height: 1.65;
  margin-bottom: 28px;
}

.bullet-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.bullet-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 16px;
  line-height: 1.5;
  font-weight: 400;
}

.bullet-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .feature-inner {
    grid-template-columns: 1fr;
  }
  .feature-inner.reverse {
    direction: ltr;
  }
  .mockup-col {
    order: 1;
  }
}
</style>
