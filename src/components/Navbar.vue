<template>
  <nav class="navbar">
    <div class="logo">
      <h1>Taxi y Express Luis Rojas</h1>
    </div>
    
    <div class="menu-toggle" @click="toggleMenu">
      <span :class="{ 'open': isMenuOpen }"></span>
      <span :class="{ 'open': isMenuOpen }"></span>
      <span :class="{ 'open': isMenuOpen }"></span>
    </div>

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

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
  isMenuOpen.value = false;
};
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  background-color: #1a1a1a;
  color: #ffffff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 5%;
  box-sizing: border-box;
  z-index: 1000;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.logo h1 {
  font-size: 1.5rem;
  margin: 0;
  color: #f39c12;
  letter-spacing: 1px;
  font-weight: 700;
}

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

.nav-links {
  list-style: none;
  display: flex;
  gap: 2.5rem;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: #ffffff;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  transition: color 0.3s ease;
}

.nav-links a:hover {
  color: #f39c12; 
}

@media (max-width: 768px) {
  .logo h1 {
    font-size: 1.2rem;
  }

  .menu-toggle {
    display: flex;
    z-index: 1001;
  }

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

  .nav-links {
    position: absolute;
    top: 80px;
    right: -100%;
    width: 100%;
    height: calc(100vh - 80px);
    background-color: #1a1a1a;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding-top: 2rem;
    gap: 2rem;
    transition: right 0.4s ease;
  }

  .nav-links.nav-active {
    right: 0; 
  }

  .nav-links a {
    font-size: 1.3rem;
  }
}
</style>
