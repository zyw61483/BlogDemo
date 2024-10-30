<script setup>
import { ref, computed } from 'vue'
import Temp from './components/Temp.vue'
import Nav from './components/Nav.vue';
import Blog from './components/Blog.vue';
import Home from './components/Home.vue';
import Aboutme from './components/Aboutme.vue';

const routes = {
  '/': Home,
  '/home': Home,
  '/blog': Blog,
  '/aboutme': Aboutme,
  '/other': Temp
}
const currentPath = ref(window.location.hash)
window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})
const isHome = ref(true)
const currentView = computed(() => {
  console.log(currentPath.value.slice(1));
  isHome.value = currentPath.value.slice(1) === '/home' || currentPath.value.slice(1) === ''
  console.log(currentPath.value.slice(1));
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
</script>

<template>
  <div class="flex-container" :class="{ home: isHome }">
    <Nav :isHome="isHome"></Nav>
    <component :is="currentView" />
  </div>
</template>

<style>
.home {
  background-image: url('https://api.hn/bing.php?rand=true');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: auto;
}

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
  justify-content: flex-start;
}
</style>