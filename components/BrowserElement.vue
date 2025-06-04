<script setup lang="ts">
import { computed, ref } from 'vue'

// Neon color suggestions:
// bg-gradient-to-r from-[#00f0ff] to-[#00bfff] border-[#00f0ff] (neon cyan/blue)
const props = defineProps({
  label: { type: String, required: true },
  heightFraction: { type: Number, required: true }, // 1, 2, 3, 4
  color: { type: String, default: 'bg-gradient-to-r from-[#00f0ff] to-[#00bfff]' } // neon blue/cyan gradient
})

// BrowserContainer height: 390px, inner padding: 1rem (16px) top+bottom = 32px
// Available height: 390 - 32 = 358px
const containerHeight = 390
const verticalPadding = 32
const availableHeight = containerHeight - verticalPadding

const elementHeight = computed(() => `${availableHeight * (props.heightFraction / 6)}px`)

const elementRef = ref<HTMLElement | null>(null)
const isBouncing = ref(false)
const overlayActive = ref(false)

function animateElement() {
  isBouncing.value = false
  void elementRef.value?.offsetWidth // force reflow
  isBouncing.value = true
  overlayActive.value = true
  setTimeout(() => {
    isBouncing.value = false
  }, 800)
  setTimeout(() => {
    overlayActive.value = false
  }, 700)
}
</script>

<template>
  <div
    ref="elementRef"
    :class="[
      'w-full flex items-center justify-center rounded-xl shadow-sm select-none relative cursor-pointer border-2 border-[#00f0ff]',
      color,
      { 'scale-bounce': isBouncing }
    ]"
    :style="{ height: elementHeight, marginBottom: '12px', boxShadow: '0 0 8px 2px #00f0ff, 0 0 2px 0.5px #00bfff' }"
    @click="animateElement"
  >
    <!-- Neon cyan highlight overlay -->
    <div
      class="absolute inset-0 pointer-events-none rounded-xl overlay"
      :class="{ 'overlay-active': overlayActive }"
    ></div>
    <span class="text-[#0a2233] font-bold text-center w-full z-10">{{ label }}</span>
    <slot />
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
  background: rgba(0,255,255,0.22);
  opacity: 0;
  filter: blur(2px);
  box-shadow: 0 0 6px 2px #00f0ff;
  transition: opacity 0.7s cubic-bezier(.22,1.61,.36,1);
}
.overlay-active {
  opacity: 0.18;
}
</style> 