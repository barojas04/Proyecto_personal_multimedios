<template>
  <section id="destinos" class="destinos-section">
    <div class="container">
      <h2 class="section-title">Cobertura Nacional</h2>
      <div class="destinos-grid">
        <div class="destino-card" @click="openModal('playas', 'Playas de Guanacaste')">
          <div class="card-inner">
            <h3>Traslados a Playas</h3>
            <p>Tamarindo, Flamingo, Conchal y principales costas de Guanacaste. (Ver fotos)</p>
          </div>
        </div>
        <div class="destino-card" @click="openModal('sanjose', 'Ciudad de San José')">
          <div class="card-inner">
            <h3>Viajes Largos</h3>
            <p>Conexiones a San José, Aeropuerto Internacional Daniel Oduber y más. (Ver fotos)</p>
          </div>
        </div>
        <div class="destino-card" @click="openModal('santacruz', 'Santa Cruz y Alrededores')">
          <div class="card-inner">
            <h3>Servicios Locales</h3>
            <p>Movilidad rápida y segura dentro de Santa Cruz y comunidades aledañas. (Ver fotos)</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal Elegante -->
    <div class="modal-overlay" :class="{ 'active': showModal }" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closeModal">&times;</button>
        <h3 class="modal-title">{{ modalTitle }}</h3>
        <div class="modal-grid">
          <img v-for="(img, idx) in selectedImages" :key="idx" :src="img" class="modal-img" alt="Foto del destino" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const showModal = ref(false);
const selectedImages = ref([]);
const modalTitle = ref('');

const destinosImages = {
  playas: [
    'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1519046904884-53103b34b206?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1499793983690-e29da59ef1c2?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1506501139174-099022df5260?auto=format&fit=crop&w=800&q=80'
  ],
  sanjose: [
    'https://images.unsplash.com/photo-1477959858617-67f85cf4f1df?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1449824913935-59a10b8d2000?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1480714378408-67cf0d13bc1b?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1494522855154-9297ac14b55f?auto=format&fit=crop&w=800&q=80'
  ],
  santacruz: [
    'https://images.unsplash.com/photo-1511884642898-4c92249e20b6?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1519331379826-f10be5486c6f?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1465146344425-f00d5f2c8f07?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1433086966358-54859d0ed716?auto=format&fit=crop&w=800&q=80'
  ]
};

const openModal = (id, title) => {
  selectedImages.value = destinosImages[id];
  modalTitle.value = title;
  showModal.value = true;
  document.body.style.overflow = 'hidden';
};

const closeModal = () => {
  showModal.value = false;
  document.body.style.overflow = '';
};
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

/* Modal */
.modal-overlay {
  position: fixed; top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.9);
  z-index: 9999;
  display: flex; justify-content: center; align-items: center;
  opacity: 0; pointer-events: none;
  transition: opacity 0.4s ease;
  backdrop-filter: blur(8px);
}
.modal-overlay.active { opacity: 1; pointer-events: auto; }
.modal-content {
  background: #111; padding: 3rem; border-radius: 12px;
  max-width: 900px; width: 90%; max-height: 90vh; overflow-y: auto;
  position: relative;
  transform: translateY(30px) scale(0.95);
  transition: all 0.4s ease;
  border: 1px solid #333;
}
.modal-overlay.active .modal-content { transform: translateY(0) scale(1); }
.close-btn {
  position: absolute; top: 1rem; right: 1.5rem; background: none; border: none;
  font-size: 2.5rem; color: #FFF; cursor: pointer; transition: color 0.3s ease;
}
.close-btn:hover { color: #D4AF37; }
.modal-title { color: #D4AF37; font-size: 2rem; margin-top: 0; margin-bottom: 2rem; font-weight: 600; text-align: center; border-bottom: 1px solid #333; padding-bottom: 1rem; }
.modal-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; }
.modal-img { width: 100%; height: 220px; object-fit: cover; border-radius: 8px; box-shadow: 0 5px 15px rgba(0,0,0,0.5); transition: transform 0.4s ease; }
.modal-img:hover { transform: scale(1.05); }
</style>
