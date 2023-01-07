<script setup>

import Home from './Home.vue'
import About from './About.vue'
import NotFound from './NotFound.vue'
import { computed, ref } from 'vue';

const vm = ref(window.location.hash)

const routers = {
  '/' : Home,
  '/about' : About
}

window.addEventListener('hashchange', () => {
  vm.value = window.location.hash
})

const ver = computed(() => routers[vm.value.slice(1)] || NotFound)

</script>


<template>
  <a href="#/">Home</a> |
  <a href="#/about">about</a> |
  <a href="#/not-exist">exist</a>
  <component :is="ver" />
</template>

