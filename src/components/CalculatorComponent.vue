<script setup>
import { ref } from 'vue'

const input = ref(0)
const buttons = ref([
  'c',
  'bs',
  '%',
  '/',
  '7',
  '8',
  '9',
  'x',
  '4',
  '5',
  '6',
  '-',
  '1',
  '2',
  '3',
  '+',
  '00',
  '0',
  '.',
  '='
])
const operands = ref(['1', '2', '3', '4', '5', '6', '7', '8', '9', '0', '00', '.'])

function handleClick(key) {}
</script>

<template>
  <div class="p-6 sm:p-8 flex flex-col gap-y-8">
    <input
      v-model="input"
      class="bg-transparent p-4 outline-0 rounded-3xl text-4xl text-white"
      dir="rtl"
    />

    <div class="grid grid-cols-4 gap-6">
      <button
        v-for="button in buttons"
        :key="button"
        class="flex justify-center items-center w-14 h-14 sm:w-20 sm:h-20 rounded-full bg-[#3a3f42] shadow-md text-lg sm:text-2xl text-red-500 font-medium"
        :class="{
          'bg-[#2f3336] text-white': operands.includes(button),
          'bg-red-500 !text-gray-900': button === '='
        }"
        @click="handleClick(button)"
      >
        {{ button.toUpperCase() }}
      </button>
    </div>
  </div>
</template>
