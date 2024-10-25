<script setup>
import { ref,onMounted,onUnmounted } from "vue"
const count = ref(0)
const flag = ref(true)
const temp = ref({ status: 0 })
const date = ref(new Date().toLocaleString('zh-CN', {
  year: 'numeric',
  month: '2-digit',
  day: '2-digit',
  hour: '2-digit',
  minute: '2-digit',
  second: '2-digit',
  hour12: false,
}).replace(/\//g, '-'))
const updateTime = () => {
  date.value = new Date().toLocaleString('zh-CN', {
  year: 'numeric',
  month: '2-digit',
  day: '2-digit',
  hour: '2-digit',
  minute: '2-digit',
  second: '2-digit',
  hour12: false,
}).replace(/\//g, '-');
};

onMounted(() => {
  const timer = setInterval(updateTime, 1000);
  onUnmounted(() => clearInterval(timer));
});
let { status } = temp.value
status++
console.log("status:" + status)
function increment() {
  count.value++
  flag.value = count.value % 2 === 0
}
function tip() {
  alert('xxx')
}


const objectOfAttrs = ref({
  id: 'container',
  class: 'wrapper',
  style: 'background-color:green;height: 100px'
})

const isGreen = ref(true)

function toggleColor() {
  isGreen.value = !isGreen.value
  objectOfAttrs.value.style = `background-color:${isGreen.value ? 'green' : 'red'};height: 100px`
}

function changeToBlue() {
  objectOfAttrs.value.style = 'background-color:blue;height: 100px'
  isGreen.value = false
}
</script>

<template>
  <button @click="increment">count is :{{ count + 1 }}</button>
  <div v-if="flag">hello : {{ flag }}</div>
  <div v-bind="objectOfAttrs" @click="tip"></div>
  <button @click="toggleColor">切换颜色</button>
  <button @click="changeToBlue">改为蓝色</button>
  {{ temp }}
  {{ date }}
</template>