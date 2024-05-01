<script setup>
import { ref } from 'vue'

const firstValue = ref('')
const secondValue = ref('')
const buttons = ref([
  'C',
  'BS',
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
const operatorKey = ref('')
const calculated = ref(false)

function handleClick(key) {
  switch (key) {
    case '00':
    case '0':
    case '1':
    case '2':
    case '3':
    case '4':
    case '5':
    case '6':
    case '7':
    case '8':
    case '9':
    case '.':
      addOperand(key)
      break
    case '+':
    case '-':
    case '/':
    case 'x':
      addOperator(key)
      break
    case '=':
      equal()
      break
    case 'C':
      clear()
      break
    case 'BS':
      backspace()
      break
    case '%':
      percent()
      break
  }
}

function addOperand(key) {
  secondValue.value += key
}

function addOperator(key) {
  operatorKey.value = key
  setFirstOperand()
}

function equal() {
  switch (operatorKey.value) {
    case '+':
      secondValue.value = `${parseFloat(firstValue.value) + parseFloat(secondValue.value)}`
      calculated.value = true
      break
    case '-':
      secondValue.value = `${parseFloat(firstValue.value) - parseFloat(secondValue.value)}`
      calculated.value = true
      break
    case '/':
      secondValue.value = `${parseFloat(firstValue.value) / parseFloat(secondValue.value)}`
      calculated.value = true
      break
    case 'x':
      secondValue.value = `${parseFloat(firstValue.value) * parseFloat(secondValue.value)}`
      calculated.value = true
      break
  }
}

function clear() {
  secondValue.value = ''
  firstValue.value = ''
  operatorKey.value = ''
}

function backspace() {
  secondValue.value = secondValue.value.slice(0, -1)
}

function percent() {
  secondValue.value = (Number(secondValue.value) / 100).toString()
}

function setFirstOperand() {
  if (secondValue.value) {
    firstValue.value = secondValue.value
    secondValue.value = ''
  }
}
</script>

<template>
  <div class="p-6 sm:p-8 flex flex-col gap-y-8">
    <div class="flex flex-col gap-y-1" dir="rtl">
      <span class="text-gray-500">
        {{ calculated ? secondValue : '' }} {{ operatorKey }} {{ firstValue }}
      </span>

      <span class="text-4xl text-white">{{ secondValue || 0 }}</span>
    </div>

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
        {{ button }}
      </button>
    </div>
  </div>
</template>
