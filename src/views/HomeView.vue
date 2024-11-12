<!-- eslint-disable vue/block-lang -->
<template>
  <div class="w-full p-5 sm:p-8 md:p-12">
    <div class="flex justify-between items-center my-5 flex-wrap">
      <h5 class="mb-3 text-lg">Menu</h5>
      <div class="flex gap-4 flex-wrap">
        <select
          v-model="selectedCategory"
          class="outline-none border border-gray-300 rounded-sm p-1"
        >
          <option value="" selected>Categories: All</option>
          <option
            v-for="category in data.map((cat) => cat.category)"
            :key="category"
            :value="category"
          >
            {{ category }}
          </option>
        </select>
        <div class="relative border border-gray-300 rounded-sm p-1">
          <input
            v-model="searchQuery"
            type="text"
            placeholder="Search"
            class="border-0 outline-none"
          />
          <IconSearch class="absolute left-[85%] top-[20%]" />
        </div>
      </div>
    </div>
    <BaseAccordion
      v-for="(category, index) in filteredData"
      :key="index"
      :title="category.category"
    >
      <slot>
        <div class="flex gap-4 flex-wrap">
          <div
            v-for="(item, ind) in category.items"
            :key="ind"
            class="relative rounded-md border border-gray-300 w-[100%] sm:w-[48%] md:w-[30%] lg:w-[32%] flex flex-col"
          >
            <img :src="item.img" :alt="item.name" class="w-[100%] h-[300px]" />
            <input
              v-model="item.checked"
              @change="calculateTotal"
              type="checkbox"
              class="absolute top-[3%] left-[3%] w-[8%] h-[4%]"
            />
            <div class="mt-2 ml-2">
              <p class="font-bold">{{ item.name }}</p>
              <p class="text-gray-400">
                {{ item.description }}
              </p>
              <p class="font-bold text-blue-500 mb-4">${{ item.price }}</p>
              <div class="flex flex-col w-min mb-2">
                <span class="text-gray-400">Quantity</span>
                <select
                  v-model="item.quantity"
                  @change="calculateTotal"
                  class="outline-none border border-gray-300 rounded-sm p-1"
                >
                  <option v-for="q in 5" :key="q" :value="q">{{ q }}</option>
                </select>
              </div>
            </div>
          </div>
        </div>
      </slot>
    </BaseAccordion>
    <!-- {{ totalPrice }} -->
    <BaseToaster :message="`Your total price is: $${totalPrice}`" :duration="5000" />
  </div>
</template>

<script lang="ts" setup>
import { ref, computed } from 'vue'
import BaseAccordion from '@/components/base/BaseAccordion.vue'
import BaseToaster from '@/components/base/BaseToaster.vue'
import IconSearch from '../components/icons/IconSearch.vue'

import data from '../Data/data.json'
const searchQuery = ref('')
const selectedCategory = ref('')
const totalPrice = ref(0)
const filteredData = computed(() => {
  return (
    data
      .filter((category) => !selectedCategory.value || category.category === selectedCategory.value)
      .map((category) => ({
        category: category.category,
        items: category.items.filter(
          (item) =>
            item.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
            item.description.toLowerCase().includes(searchQuery.value.toLowerCase()),
        ),
      }))
      // Remove empty categories
      .filter((category) => category.items.length > 0)
  )
})
// Calculate the total price
function calculateTotal() {
  let total = 0
  data.forEach((category) => {
    category.items.forEach((item) => {
      if (item.checked) {
        total += item.price * item.quantity
      }
    })
  })
  // Display total in a toast message
  totalPrice.value = total
}
console.log(data)
</script>
