<script setup>
defineProps({
  size: { type: Number, default: 34 }
})
</script>

<template>
  <div class="brand" :style="{ height: size + 'px' }">
    <svg :height="size" viewBox="0 0 270 56" fill="none" xmlns="http://www.w3.org/2000/svg" aria-label="MusicA" role="img">
      <defs>
        <linearGradient id="mg" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0%" stop-color="#1f6df0" />
          <stop offset="55%" stop-color="#2aa7d8" />
          <stop offset="100%" stop-color="#14b8a6" />
        </linearGradient>
      </defs>
      <text x="0" y="42" font-family="Plus Jakarta Sans, Inter, sans-serif" font-size="40" font-weight="800" fill="#0c1e33" letter-spacing="1">MUSIC</text>
      <!-- Letter A drawn manually -->
      <path d="M170 44 L185 10 L200 44 M176 32 H194" stroke="#0c1e33" stroke-width="5.5" stroke-linejoin="round" stroke-linecap="round" fill="none"/>
      <!-- Checkmark accent, blue-teal gradient, positioned to the right of the A -->
      <path d="M212 30 L224 42 L246 12" stroke="url(#mg)" stroke-width="6.5" stroke-linecap="round" stroke-linejoin="round" fill="none" />
    </svg>
  </div>
</template>

<style scoped>
.brand { display: inline-flex; align-items: center; }
.brand svg { display: block; }
</style>
