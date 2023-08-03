<script setup>
import Countdown from './components/Countdown.vue'
</script>

<template>
  <Countdown class="text-4xl lg:text-7xl w-full h-full" :deadline="'2023-10-03T12:40:00'"/>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
