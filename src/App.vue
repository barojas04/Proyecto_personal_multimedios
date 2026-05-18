<script setup>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Flota from './components/Flota.vue'
import Destinos from './components/Destinos.vue'
import Testimonios from './components/Testimonios.vue'
import Contacto from './components/Contacto.vue'
</script>

<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <Flota />
    <Destinos />
    <Testimonios />
    <Contacto />
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', 'Inter', 'Roboto', sans-serif;
  background-color: #000;
  scroll-behavior: smooth;
  color: #111111;
  overflow-x: hidden;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
