<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{ success: boolean; msg: string; time: number }>()

var shown = ref(false)

let debounceTimer: number | undefined = undefined
watch(props, () => {
    shown.value = true
    if (debounceTimer) clearTimeout(debounceTimer)
    debounceTimer = setTimeout(() => {
      shown.value = false
    }, 4000)
  },
  { deep: true }
)
</script>

<template>
  <div class="fixed top-0 right-0 z-50 m-2 sm:m-5 px-3 py-2 rounded-lg shadow-lg text-white font-semibold max-w-[100vw] transition-[right]"
    :class="{ 'bg-green-500': props.success, 'bg-red-500': !props.success }"
    :style="{ right: shown ? '0' : 'calc(-100% - 12px)' }">
    {{ props.msg }}
  </div>
</template>
