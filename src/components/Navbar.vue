<template>
  <nav class="navbar">
    <div class="logo">
      <h1>Taxi y Express Luis Rojas</h1>
    </div>
    <ul class="nav-links">
      <li><a href="#inicio">Inicio</a></li>
      <li><a href="#servicios">Servicios</a></li>
      <li><a href="#flota">Flota</a></li>
      <li><a href="#testimonios">Testimonios</a></li>
      <li><a href="#contacto">Contacto</a></li>
    </ul>
  </nav>
</template>

<script setup>
// Al ser un componente puramente visual en esta etapa,
// no necesitamos lógica compleja. Vue 3 nos permite
// dejar el script setup sin contenido si no declaramos variables.
</script>

<style scoped>
/* Contenedor principal de navegación */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  background-color: #1a1a1a; /* Fondo oscuro profesional */
  color: #ffffff;
  display: flex;
  justify-content: space-between; /* Logo a la izq, links a la der */
  align-items: center;
  padding: 0 5%;
  box-sizing: border-box;
  z-index: 1000; /* Siempre encima del resto del contenido */
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3); /* Sombra para resaltar */
}

/* Estilo del logotipo / nombre */
.logo h1 {
  font-size: 1.5rem;
  margin: 0;
  color: #f39c12; /* Color amarillo/naranja evocando servicio de taxi */
  letter-spacing: 1px;
  font-weight: 700;
}

/* Lista de enlaces */
.nav-links {
  list-style: none;
  display: flex;
  gap: 2.5rem;
  margin: 0;
  padding: 0;
}

/* Enlaces individuales */
.nav-links a {
  color: #ffffff;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  transition: color 0.3s ease; /* Transición suave para el hover */
}

/* Efecto hover interactivo */
.nav-links a:hover {
  color: #f39c12; 
}
</style>
