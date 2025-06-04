<script setup lang="ts">
import { ref } from 'vue'

const containerRef = ref<HTMLElement | null>(null)
const isBouncing = ref(false)
const overlayActive = ref(false)

function animateBorder() {
  isBouncing.value = false
  void containerRef.value?.offsetWidth // force reflow
  isBouncing.value = true
  overlayActive.value = true
  setTimeout(() => {
    isBouncing.value = false
  }, 800)
  setTimeout(() => {
    overlayActive.value = false
  }, 700)
}

function onBorderClick(e: MouseEvent) {
  const content = containerRef.value?.querySelector('.browser-content')
  if (content && content.contains(e.target as Node)) return
  animateBorder()
}
</script>

<template>
  <div class="flex flex-col items-center">
    <div
      ref="containerRef"
      :class="[
        'w-60 h-[390px] bg-[#18181b] rounded-2xl shadow-lg border-4 border-cyan-500 hover:border-cyan-400 transition-colors duration-200 overflow-hidden relative cursor-pointer',
        { 'scale-bounce': isBouncing }
      ]"
      tabindex="0"
      @click="onBorderClick"
    >
      <!-- Highlight overlay -->
      <div
        class="absolute inset-0 pointer-events-none rounded-2xl overlay"
        :class="{ 'overlay-active': overlayActive }"
      ></div>
      <!-- Browser header bar -->
      <div class="h-8 bg-[#23272f] border-b border-cyan-900 flex items-center px-4">
        <div class="w-4 h-4 bg-cyan-700 rounded-full mr-2"></div>
        <div class="w-24 h-3 bg-cyan-900 rounded"></div>
      </div>
      <!-- Content area with slot and padding -->
      <div class="flex-1 p-4 flex flex-col gap-4 browser-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>
.scale-bounce {
  animation: bounce-scale 0.8s cubic-bezier(.22,1.61,.36,1) both;
}
@keyframes bounce-scale {
  0%   { transform: scale(1); }
  20%  { transform: scale(1.07); }
  100% { transform: scale(1); }
}
.overlay {
  background: rgba(0,255,255,0.55);
  opacity: 0;
  filter: blur(2px);
  box-shadow: 0 0 8px 2px #00f0ff, 0 0 2px 0.5px #00bfff;
  transition: opacity 0.7s cubic-bezier(.22,1.61,.36,1);
}
.overlay-active {
  opacity: 0.18;
}
</style> 