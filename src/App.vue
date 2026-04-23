<script setup>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
</script>

<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <!-- Las futuras secciones (Servicios, Flota, Testimonios) irán aquí debajo -->
  </div>
</template>

<style>
/* Estilos globales para resetear márgenes y fuentes en toda la página */
body {
  margin: 0;
  padding: 0;
  font-family: 'Inter', 'Roboto', 'Helvetica Neue', sans-serif;
  background-color: #f5f5f5;
  scroll-behavior: smooth; /* Para que el scroll hacia las anclas sea suave */
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
