<template>
  <section id="inicio" class="hero">
    <div class="video-container">
      <video autoplay loop muted playsinline class="background-video" poster="/hero_bg.png">
        <source src="https://videos.pexels.com/video-files/3163534/3163534-uhd_2560_1440_30fps.mp4" type="video/mp4" />
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
  document.getElementById('contacto').scrollIntoView({ behavior: 'smooth' });
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&display=swap');

.hero {
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  font-family: 'Poppins', sans-serif;
}

.video-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -2;
  background-color: #000;
  background-image: url('/hero_bg.png');
  background-size: cover;
  background-position: center;
}

.background-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(20%) contrast(1.1) brightness(0.8); 
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.85) 0%, rgba(0, 0, 0, 0.4) 100%); 
  z-index: -1; 
}

.hero-content {
  text-align: center;
  color: #FFF;
  z-index: 1;
  padding: 0 20px;
  max-width: 900px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.title {
  font-size: 4.5rem;
  font-weight: 800; 
  margin-bottom: 1.5rem;
  letter-spacing: 2px;
  line-height: 1.1;
  text-transform: uppercase;
  background: linear-gradient(to right, #FFF, #D4AF37);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0px 10px 20px rgba(0,0,0,0.5));
}

.subtitle {
  font-size: 1.4rem;
  font-weight: 300; 
  margin-bottom: 3.5rem;
  line-height: 1.6;
  color: #EAEAEA;
  max-width: 700px;
  text-shadow: 0 2px 4px rgba(0,0,0,0.8);
}

.cta-button {
  background-color: rgba(0, 0, 0, 0.5);
  color: #FFF; 
  border: 2px solid #D4AF37;
  padding: 16px 48px;
  font-size: 1.1rem;
  font-weight: 600;
  letter-spacing: 2px;
  border-radius: 8px; /* Redondeado sutil 8-12px */
  cursor: pointer;
  transition: all 0.4s ease;
  text-transform: uppercase;
  box-shadow: 0 4px 15px rgba(0,0,0,0.3);
  backdrop-filter: blur(5px);
}

.cta-button:hover {
  background-color: #D4AF37;
  color: #000;
  transform: translateY(-5px) scale(1.02);
  box-shadow: 0 15px 30px rgba(212, 175, 55, 0.4);
  border-color: #FFF;
}

.cta-button:active {
  transform: translateY(0);
}

@media (max-width: 768px) {
  .title {
    font-size: 2.8rem;
  }
  .subtitle {
    font-size: 1.1rem;
    margin-bottom: 2.5rem;
  }
  .cta-button {
    padding: 14px 30px;
    width: 100%;
    max-width: 300px;
  }
}
</style>
