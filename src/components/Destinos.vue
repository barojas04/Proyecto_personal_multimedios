<template>
  <section id="destinos" class="destinos-section">
    <div class="container">
      <h2 class="section-title">Cobertura Nacional</h2>
      <div class="destinos-grid">
        <div class="destino-card">
          <div class="card-inner">
            <h3>Traslados a Playas</h3>
            <p>Tamarindo, Flamingo, Conchal y principales costas de Guanacaste.</p>
          </div>
        </div>
        <div class="destino-card">
          <div class="card-inner">
            <h3>Viajes Largos</h3>
            <p>Conexiones a San José, Aeropuerto Internacional Daniel Oduber y más.</p>
          </div>
        </div>
        <div class="destino-card">
          <div class="card-inner">
            <h3>Servicios Locales</h3>
            <p>Movilidad rápida y segura dentro de Santa Cruz y comunidades aledañas.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const destinosImages = ref({});
const baseUrl = import.meta.env.BASE_URL;

onMounted(async () => {
  try {
    const response = await fetch(baseUrl + 'data.json');
    const data = await response.json();
    destinosImages.value = data.destinosImages;
  } catch (error) {
    console.error('Error cargando destinosImages:', error);
  }
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

.destinos-section {
  background-color: #FFF;
  background-image: url('/subtle_texture.png');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  padding: 8rem 2rem;
  color: #000;
  font-family: 'Poppins', sans-serif;
  position: relative;
}
.destinos-section::before {
  content: '';
  position: absolute;
  top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(255, 255, 255, 0.85);
  z-index: 0;
}

.container { max-width: 1000px; margin: 0 auto; position: relative; z-index: 1; }
.section-title { text-align: center; font-size: 2.8rem; font-weight: 600; margin-bottom: 5rem; letter-spacing: 2px; text-transform: uppercase; }
.section-title::after { content: ''; display: block; width: 60px; height: 3px; background-color: #D4AF37; margin: 1rem auto 0; }
.destinos-grid { display: flex; flex-direction: column; gap: 2.5rem; }

.destino-card {
  background-color: rgba(255, 255, 255, 0.95);
  border-radius: 12px; 
  border-left: 4px solid #111;
  box-shadow: 0 5px 20px rgba(0,0,0,0.05);
  transition: all 0.4s ease;
  overflow: hidden;
  backdrop-filter: blur(10px);
  cursor: pointer;
}
.destino-card:hover {
  transform: translateX(15px) scale(1.01);
  box-shadow: 0 15px 30px rgba(0,0,0,0.15);
  border-left: 8px solid #D4AF37;
}
.card-inner { padding: 3rem; }
.destino-card h3 { font-size: 1.5rem; font-weight: 600; margin: 0 0 1rem 0; letter-spacing: 1px; color: #000; transition: color 0.4s ease; }
.destino-card:hover h3 { color: #D4AF37; }
.destino-card p { color: #444; margin: 0; line-height: 1.8; font-weight: 400; font-size: 1.1rem; }
</style>
