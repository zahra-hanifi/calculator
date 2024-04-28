<script setup>
import Calculator from '@/components/CalculatorComponent.vue'
</script>

<template>
  <div class="bg-gray-950 min-h-screen flex justify-center items-center p-8">
    <div class="w-full md:w-1/2 2xl:w-1/4 flex flex-col gap-y-8">
      <div class="flex justify-center items-center gap-x-1 flex-wrap">
        <span class="text-gray-300">A Vue calculator Application by</span>

        <a href="https://github.com/zahra-hanifi/" target="_blank" class="font-bold text-white">
          Zahra Hanifi
        </a>
      </div>

      <div class="bg-[#2a2d2e] shadow rounded-2xl">
        <Calculator />
      </div>
    </div>
  </div>
</template>
