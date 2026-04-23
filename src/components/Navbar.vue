<template>
  <nav class="navbar">
    <div class="logo">
      <h1>Taxi y Express Luis Rojas</h1>
    </div>
    
    <!-- Botón de menú hamburguesa (visible solo en móviles) -->
    <div class="menu-toggle" @click="toggleMenu">
      <span :class="{ 'open': isMenuOpen }"></span>
      <span :class="{ 'open': isMenuOpen }"></span>
      <span :class="{ 'open': isMenuOpen }"></span>
    </div>

    <!-- Lista de enlaces, con clase condicional para mostrar/ocultar en móvil -->
    <ul class="nav-links" :class="{ 'nav-active': isMenuOpen }">
      <li><a href="#inicio" @click="closeMenu">Inicio</a></li>
      <li><a href="#servicios" @click="closeMenu">Servicios</a></li>
      <li><a href="#flota" @click="closeMenu">Flota</a></li>
      <li><a href="#testimonios" @click="closeMenu">Testimonios</a></li>
      <li><a href="#contacto" @click="closeMenu">Contacto</a></li>
    </ul>
  </nav>
</template>

<script setup>
import { ref } from 'vue';

// Variable reactiva para controlar el estado del menú en móviles
const isMenuOpen = ref(false);

// Función para alternar el menú (abrir/cerrar)
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// Función para cerrar el menú al hacer clic en un enlace
const closeMenu = () => {
  isMenuOpen.value = false;
};
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

/* Ocultar el botón de menú en escritorio por defecto */
.menu-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
}

.menu-toggle span {
  width: 25px;
  height: 3px;
  background-color: #ffffff;
  border-radius: 3px;
  transition: all 0.3s ease;
}

/* Lista de enlaces (Escritorio) */
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

/* === MEDIA QUERIES PARA MÓVILES (Max 768px) === */
@media (max-width: 768px) {
  /* Ajustar tamaño del logo para que no ocupe tanto espacio */
  .logo h1 {
    font-size: 1.2rem;
  }

  /* Mostrar el botón de hamburguesa */
  .menu-toggle {
    display: flex;
    z-index: 1001; /* Para que el icono quede sobre el menú desplegado si se cruzan */
  }

  /* Animación básica del icono hamburguesa al abrir */
  .menu-toggle span.open:nth-child(1) {
    transform: translateY(8px) rotate(45deg);
    background-color: #f39c12;
  }
  .menu-toggle span.open:nth-child(2) {
    opacity: 0;
  }
  .menu-toggle span.open:nth-child(3) {
    transform: translateY(-8px) rotate(-45deg);
    background-color: #f39c12;
  }

  /* Configuración del menú vertical para móvil */
  .nav-links {
    position: absolute;
    top: 80px; /* Empieza justo debajo del navbar */
    right: -100%; /* Oculto fuera de la pantalla a la derecha inicialmente */
    width: 100%;
    height: calc(100vh - 80px); /* Ocupa el resto de la pantalla */
    background-color: #1a1a1a;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding-top: 2rem;
    gap: 2rem;
    transition: right 0.4s ease; /* Animación suave al deslizarse hacia adentro/afuera */
  }

  /* Clase que se activa cuando isMenuOpen es true, deslizando el menú a la vista */
  .nav-links.nav-active {
    right: 0; 
  }

  /* Ajustamos un poco el tamaño de letra de los enlaces en el menú móvil */
  .nav-links a {
    font-size: 1.3rem;
  }
}
</style>
