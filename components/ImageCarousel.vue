<script setup lang="ts">
import { ref, onMounted, onUnmounted, computed } from 'vue'

interface Props {
  images: string[]
  interval?: number
  /**
   * How the image should fit its container.
   * - 'fill': object-fill
   * - 'contain': object-contain
   * - 'cover': object-cover
   * - 'none': object-none
   * - 'scale-down': object-scale-down
   */
  fit?: 'fill' | 'contain' | 'cover' | 'none' | 'scale-down'
  align?: 'center' | 'top left' | 'top right' | 'bottom left' | 'bottom right'
  full?: boolean
  maxHeight?: string
  /** Explicit height for the carousel (e.g. '400px', '100%'). */
  height?: string
  /** Explicit width for the carousel (e.g. '600px', '100%'). */
  width?: string
}
const props = defineProps<Props>()

const current = ref(0)
let timer: number | undefined

onMounted(() => {
  timer = window.setInterval(() => {
    current.value = (current.value + 1) % props.images.length
  }, props.interval ?? 3000)
})

onUnmounted(() => {
  if (timer) clearInterval(timer)
})

const fitClass = computed(() => {
  switch (props.fit) {
    case 'fill': return 'object-fill'
    case 'contain': return 'object-contain'
    case 'cover': return 'object-cover'
    case 'none': return 'object-none'
    case 'scale-down': return 'object-scale-down'
    default: return 'object-contain'
  }
})
const alignMap: Record<string, string> = {
  'center': 'object-center',
  'top left': 'object-left-top',
  'top right': 'object-right-top',
  'bottom left': 'object-left-bottom',
  'bottom right': 'object-right-bottom',
}
const alignClass = computed(() => alignMap[props.align ?? 'center'] ?? 'object-center')
const sizeClass = computed(() => props.full ? 'w-full h-full' : 'max-h-80 max-w-full')
const rootStyle = computed(() => {
  const style: Record<string, string> = {}
  if (props.height) style.height = props.height
  if (props.width) style.width = props.width
  if (!props.height && props.maxHeight) style.maxHeight = props.maxHeight
  else if (!props.height && !props.maxHeight) style.maxHeight = 'calc(100% - 4rem)'
  return style
})
</script>

<template>
  <div
    class="flex items-start justify-start box-border overflow-hidden"
    :style="rootStyle"
  >
    <img
      :src="props.images[current]"
      :class="['rounded shadow-lg transition-all duration-500', fitClass, alignClass, 'w-full max-h-full']"
      alt="carousel image"
    />
  </div>
</template> 