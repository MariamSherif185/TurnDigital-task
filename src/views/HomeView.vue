<script setup lang="ts">
import BaseAccordion from '../components/base/BaseAccordion.vue'
import IconSearch from '../components/icons/IconSearch.vue'
</script>

<template>
  <div class="w-full p-5 sm:p-8 md:p-12">
    <div class="flex justify-between items-center my-5 flex-wrap">
      <h5 class="mb-3 text-lg">Menu</h5>
      <div class="flex gap-4 flex-wrap">
        <!-- <div class="relative border border-gray-300 rounded-md p-1"> -->
        <select
          name=""
          placeholder="Search"
          id=""
          class="outline-none border border-gray-300 rounded-sm p-1"
        >
          <option value="" selected>Categories: All</option>
          <option value="">Appitizers</option>
          <option value="">Soups</option>
          <option value="">Salads</option>
          <option value="">Sandwiches</option>
        </select>
        <!-- </div> -->
        <div class="relative border border-gray-300 rounded-sm p-1">
          <input type="text" placeholder="Search" class="border-0 outline-none" />
          <IconSearch class="absolute left-[85%] top-[20%]" />
        </div>
      </div>
    </div>
    <BaseAccordion title="Appitizers" aria-title="appitizers">
      <slot>
        <div class="flex gap-4 flex-wrap">
          <div
            class="rounded-md border border-gray-300 w-[100%] sm:w-[48%] md:w-[30%] lg:w-[32%] flex flex-col"
          >
            <img src="../assets/onion-rings.jpg" alt="" class="w-[100%]" />
            <div class="mt-2 ml-2">
              <p class="font-bold">Cripsy Onion Rings</p>
              <p class="text-gray-400">
                Lorem ipsum dolor sit amet consectetur, adipisicing elit. Necessitatibus minus,
                quisquam
              </p>
              <p class="font-bold text-blue-500 mb-4">$6.00</p>
              <div class="flex flex-col w-min mb-2">
                <span class="text-gray-400">Quantity</span>
                <select name="" id="" class="outline-none border border-gray-300 rounded-sm p-1">
                  <option value="" selected>1</option>
                  <option value="">2</option>
                  <option value="">3</option>
                  <option value="">4</option>
                  <option value="">5</option>
                </select>
              </div>
            </div>
          </div>
          <div
            class="rounded-md border border-gray-300 w-[100%] sm:w-[48%] md:w-[30%] lg:w-[32%] flex flex-col"
          >
            <img src="../assets/onion-rings.jpg" alt="" class="w-[100%]" />
            <div class="mt-2 ml-2">
              <p class="font-bold">Cripsy Onion Rings</p>
              <p class="text-gray-400">
                Lorem ipsum dolor sit amet consectetur, adipisicing elit. Necessitatibus minus,
                quisquam
              </p>
              <p class="font-bold text-blue-500 mb-4">$6.00</p>
              <div class="flex flex-col w-min mb-2">
                <span class="text-gray-400">Quantity</span>
                <select name="" id="" class="outline-none border border-gray-300 rounded-sm p-1">
                  <option value="" selected>1</option>
                  <option value="">2</option>
                  <option value="">3</option>
                  <option value="">4</option>
                  <option value="">5</option>
                </select>
              </div>
            </div>
          </div>
          <div
            class="rounded-md border border-gray-300 w-[100%] sm:w-[48%] md:w-[31%] lg:w-[32%] flex flex-col"
          >
            <img src="../assets/onion-rings.jpg" alt="" class="w-[100%]" />
            <div class="mt-2 ml-2">
              <p class="font-bold">Cripsy Onion Rings</p>
              <p class="text-gray-400">
                Lorem ipsum dolor sit amet consectetur, adipisicing elit. Necessitatibus minus,
                quisquam
              </p>
              <p class="font-bold text-blue-500 mb-4">$6.00</p>
              <div class="flex flex-col w-min mb-2">
                <span class="text-gray-400">Quantity</span>
                <select name="" id="" class="outline-none border border-gray-300 rounded-sm p-1">
                  <option value="" selected>1</option>
                  <option value="">2</option>
                  <option value="">3</option>
                  <option value="">4</option>
                  <option value="">5</option>
                </select>
              </div>
            </div>
          </div>
        </div>
      </slot>
    </BaseAccordion>
    <BaseAccordion title="Soups" aria-title="soups">
      <slot> Soups</slot>
    </BaseAccordion>
    <BaseAccordion title="Salads" aria-title="salads">
      <slot> Salads</slot>
    </BaseAccordion>
    <BaseAccordion title="'Sandwiches'" aria-title="'sandwiches'">
      <slot> Sandwiches</slot>
    </BaseAccordion>
  </div>
</template>
