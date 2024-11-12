<template>
  <div
    v-if="visible"
    class="p-3 border fixed top-[15%] right-[50%] rounded-md transition-opacity duration-500 ease bg-white"
    :class="type == 'success' ? 'border-green-600 text-green-600' : 'border-red-600 text-red-600'"
  >
    {{ message }}
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import { defineProps } from 'vue'

const props = defineProps({
  message: String,
  type: {
    type: String,
    default: 'success',
  },
  duration: {
    type: Number,
    default: 3000,
  },
})

const visible = ref(false)

watch(
  () => props.message,
  (newMessage) => {
    if (newMessage) show()
  },
)

function show() {
  visible.value = true
  setTimeout(() => {
    visible.value = false
  }, props.duration)
}
</script>
