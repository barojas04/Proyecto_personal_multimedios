<template>
  <section id="inicio" class="hero">
    <div class="video-container">
      <video autoplay loop muted playsinline class="background-video">
        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4" />
        Tu navegador no soporta videos HTML5.
      </video>
    </div>
    
    <div class="overlay"></div>

    <div class="hero-content">
      <h1 class="title">Tu viaje seguro, rápido y confiable</h1>
      <p class="subtitle">Servicio de transporte y mensajería 24/7 en Santa Cruz, Guanacaste.</p>
      <button class="cta-button" @click="solicitarViaje">Solicitar Viaje</button>
    </div>
  </section>
</template>

<script setup>
const solicitarViaje = () => {
  console.log("Iniciando solicitud de viaje...");
  alert("¡Pronto podrás solicitar tu viaje por aquí!");
};
</script>

<style scoped>
.hero {
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.video-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -2;
}

.background-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6); 
  z-index: -1; 
}

.hero-content {
  text-align: center;
  color: #ffffff;
  z-index: 1;
  padding: 0 20px;
  max-width: 800px;
}

.title {
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.subtitle {
  font-size: 1.5rem;
  margin-bottom: 2.5rem;
  line-height: 1.5;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5);
}

.cta-button {
  background-color: #f39c12;
  color: #1a1a1a;
  border: none;
  padding: 15px 40px;
  font-size: 1.2rem;
  font-weight: bold;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(243, 156, 18, 0.4);
}

.cta-button:hover {
  background-color: #e67e22;
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(243, 156, 18, 0.6);
}

.cta-button:active {
  transform: translateY(0);
}

@media (max-width: 768px) {
  .hero-content {
    padding: 0 15px;
  }
  
  .title {
    font-size: 2.2rem;
  }

  .subtitle {
    font-size: 1.1rem;
    margin-bottom: 2rem;
  }

  .cta-button {
    padding: 12px 30px;
    font-size: 1.1rem;
    width: 100%;
    max-width: 300px;
  }
}
</style>
