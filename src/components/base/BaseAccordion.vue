<template>
  <div class="panel container mb-4 border-bottom-2">
    <button
      :arial-controls="'accordion-content-' + props.ariaTitle"
      :id="'accordion-control-' + props.ariaTitle"
      @click.prevent="togglePanel"
      class="p-4 w-full border-b-2 font-semibold flex items-center justify-between"
    >
      {{ props.title }}
      <span class="material-icons" v-if="showPanel"> <IconArrowUp /> </span>
      <span class="material-icons" v-else> <IconArrowDown /></span>
    </button>
    <div :aria-hidden="!showPanel" :id="'content-' + props.ariaTitle" class="p-4" v-if="showPanel">
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import IconArrowDown from '../icons/IconArrowDown.vue'
import IconArrowUp from '../icons/IconArrowUp.vue'
import { ref } from 'vue'

const props = defineProps({
  title: { type: String, required: true },
  ariaTitle: { type: String, required: true },
})
const showPanel = ref(false)
const togglePanel = () => {
  showPanel.value = !showPanel.value
}
</script>
