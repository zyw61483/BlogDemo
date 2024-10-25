<script setup>
import { ref, computed } from 'vue'
import Temp from './components/Temp.vue'
import Nav from './components/Nav.vue';
import Blog from './components/Blog.vue';
import Home from './components/Home.vue';

const routes = {
  '/': Home,
  '/home': Home,
  '/blog': Blog,
  '/other': Temp
}
const currentPath = ref(window.location.hash)
window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})
const currentView = computed(() => {
  console.log(currentPath.value.slice(1));
  
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
</script>

<template>
  <div class="flex-container">
    <Nav></Nav>
    <component :is="currentView"/>
  </div>
</template>

<style>
#app,
html,
body {
  height: 100%;
  width: 100%;
  margin: 0;
}

.flex-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
}
</style>