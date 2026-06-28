<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  target: { type: Number, required: true },
  label: { type: String, required: true },
  suffix: { type: String, default: '' }
})

const current = ref(0)
const containerRef = ref(null)
let started = false

function easeOutQuart(t) {
  return 1 - Math.pow(1 - t, 4)
}

function startCount() {
  if (started) return
  started = true
  const duration = 2200
  const startTime = Date.now()

  function tick() {
    const elapsed = Date.now() - startTime
    const progress = Math.min(elapsed / duration, 1)
    current.value = Math.round(easeOutQuart(progress) * props.target)
    if (progress < 1) requestAnimationFrame(tick)
  }
  requestAnimationFrame(tick)
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        startCount()
        observer.disconnect()
      }
    },
    { threshold: 0.5 }
  )
  if (containerRef.value) observer.observe(containerRef.value)
})
</script>

<template>
  <div ref="containerRef" class="stat-item">
    <span class="stat-number">{{ current }}{{ suffix }}</span>
    <span class="stat-label">{{ label }}</span>
  </div>
</template>

<style scoped>
.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.stat-number {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  font-size: clamp(56px, 7vw, 88px);
  font-weight: 700;
  line-height: 1;
  letter-spacing: -0.04em;
  color: #ffffff;
  font-variant-numeric: tabular-nums;
}

.stat-label {
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.45);
}
</style>
