<template>
  <img :src="src" :alt="alt" :style="logoStyle" class="corner-logo" />
</template>

<script setup>
import { computed } from 'vue'
const props = defineProps({
  src: { type: String, required: true },
  alt: { type: String, default: '' },
  height: { type: [String, Number], default: '250px' }
})

const logoStyle = computed(() => ({
  height: typeof props.height === 'number' ? props.height + 'px' : props.height
}))
</script>

<style scoped>
.corner-logo {
  position: absolute;
  top: 2rem;
  right: 2rem;
  opacity: 0.9;
  z-index: 10;
}
</style> 