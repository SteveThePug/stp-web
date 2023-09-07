<script setup>
import Navbar from './components/Navbar.vue'
import SlidingImage from './components/SlidingImage.vue'
import SlidingFont from './components/SlidingFont.vue';
</script>

<template>
  <div class="body">
    <Navbar />
    <SlidingImage />
  </div>
</template>

<style scoped>
.body {
  width: 100vw;
  height: 200vh;
  margin: 0px 0px 0px 0px;
}

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
