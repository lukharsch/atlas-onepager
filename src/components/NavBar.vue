<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import iconUrl from '../assets/appicon.png'

const scrolled = ref(false)

function onScroll() {
  scrolled.value = window.scrollY > 24
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<template>
  <nav
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="scrolled ? 'nav-scrolled' : 'bg-transparent border-b border-transparent'"
  >
    <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
      <div style="display:flex; align-items:center; gap:10px;">
        <img :src="iconUrl" alt="Atlas icon" style="width:30px; height:30px; border-radius:7px;" />
        <span
          class="text-white font-semibold text-xl tracking-tight"
          style="font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif; letter-spacing: -0.03em;"
        >
          Atlas
        </span>
      </div>

      <a href="#" class="app-store-btn-outline text-sm font-medium py-2 px-5" style="border-radius: 999px; padding: 8px 20px; font-size: 14px;">
        Download
      </a>
    </div>
  </nav>
</template>
