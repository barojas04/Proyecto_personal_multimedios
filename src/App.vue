<script setup>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
</script>

<template>
  <div class="app-container">
    <Navbar />
    <Hero />
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Inter', 'Roboto', 'Helvetica Neue', sans-serif;
  background-color: #f5f5f5;
  scroll-behavior: smooth;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
