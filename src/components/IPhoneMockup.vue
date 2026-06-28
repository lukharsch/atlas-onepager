<script setup>
import mapImage from '@/assets/screenshots/map.webp'
import statsImage from '@/assets/screenshots/stats.webp'
import timelineImage from '@/assets/screenshots/timeline.webp'
import tripDetailImage from '@/assets/screenshots/tripdetail.webp'

import {computed} from "vue";

const props = defineProps({
  label: { type: String, required: true },
  color: { type: String, default: 'dark' },
  imageUrl: { type: String, default: '' }
})

const iPhoneImage = computed(() => {
  switch (props.imageUrl) {
    case 'map':
      return mapImage
    case 'stats':
      return statsImage
    case 'timeline':
      return timelineImage
    case 'tripdetail':
      return tripDetailImage
    default:
      return ''
  }
})
</script>

<template>
  <div class="iphone-outer">
    <div class="iphone-frame frame-dark">
      <div class="iphone-screen">

        <!-- Dynamic Island -->
        <!--<div class="dynamic-island"></div>-->

        <!-- Screen body -->
        <div class="screen-body">
          <!-- REPLACE: screenshot of {{ label }} -->
          <div class="screen-placeholder">
            <div class="dynamic-island"></div>
            <div class="home-bar"></div>
            <!--<svg width="36" height="36" viewBox="0 0 36 36" fill="none" class="placeholder-icon">
              <rect width="36" height="36" rx="10" fill="currentColor" opacity="0.12"/>
              <path d="M6 28l8-10 5 6 4-5 7 9H6z" fill="currentColor" opacity="0.25"/>
              <circle cx="12" cy="15" r="2.5" fill="currentColor" opacity="0.25"/>
            </svg>
            <span class="placeholder-label">{{ label }}</span>-->
            <img :src="iPhoneImage" />
          </div>
        </div>

        <!-- Home indicator -->
        <div class="home-bar"></div>

      </div>
    </div>
  </div>
</template>

<style scoped>
.iphone-outer {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

.iphone-frame {
  position: relative;
  width: 280px;
  height: 578px;
  border-radius: 54px;
  padding: 11px;
  flex-shrink: 0;
}

.frame-dark {
  background: linear-gradient(150deg, #3a3a3c 0%, #1c1c1e 55%, #2c2c2e 100%);
  box-shadow:
    0 0 0 1px rgba(255, 255, 255, 0.10),
    0 48px 96px rgba(0, 0, 0, 0.72),
    inset 0 1px 0 rgba(255, 255, 255, 0.15);
}

.frame-light {
  background: linear-gradient(150deg, #f0f0f0 0%, #d8d8d8 55%, #e4e4e4 100%);
  box-shadow:
    0 0 0 1px rgba(0, 0, 0, 0.08),
    0 48px 96px rgba(0, 0, 0, 0.35),
    inset 0 1px 0 rgba(255, 255, 255, 0.9);
}

.iphone-screen {
  width: 100%;
  height: 100%;
  border-radius: 44px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

.frame-dark .iphone-screen {
  background: linear-gradient(165deg, #0d1117 0%, #111827 45%, #0a0f1a 100%);
}
.frame-light .iphone-screen {
  background: linear-gradient(165deg, #f5f5f7 0%, #e8e8ed 60%, #ededf0 100%);
}

.dynamic-island {
  width: 88px;
  height: 25px;
  background: #000;
  border-radius: 20px;
  margin-top: 8px;
  flex-shrink: 0;
  z-index: 2;
  position: absolute;
}

.screen-body {
  flex: 1;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.screen-placeholder {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.placeholder-icon {
  color: inherit;
}

.frame-dark .placeholder-icon { color: #ffffff; }
.frame-light .placeholder-icon { color: #1d1d1f; }

.placeholder-label {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  opacity: 0.3;
}

.frame-dark .placeholder-label { color: #ffffff; }
.frame-light .placeholder-label { color: #1d1d1f; }

.home-bar {
  width: 100px;
  height: 3px;
  border-radius: 3px;
  margin-bottom: 3px;
  opacity: 0.35;
  flex-shrink: 0;
  position: absolute;
  bottom: 0px;
}

.frame-dark .home-bar { background: #1d1d1f; }
.frame-light .home-bar { background: #1d1d1f; }
</style>
