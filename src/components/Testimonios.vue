<template>
  <section id="testimonios" class="testimonios-section">
    <div class="container">
      <h2 class="section-title">Experiencias</h2>
      <div class="testimonios-grid">
        <div class="testimonio-card" v-for="(testimonio, index) in testimonios" :key="index">
          <div class="quote-icon">“</div>
          <p class="testimonio-text">{{ testimonio.texto }}</p>
          <div class="testimonio-footer">
            <div class="client-info">
              <h4>{{ testimonio.nombre }}</h4>
              <span>{{ testimonio.rol }}</span>
            </div>
            <div class="audio-player" v-if="testimonio.audio && testimonio.audio !== ''">
              <audio :id="'audio-' + index" :src="testimonio.audio.startsWith('http') ? testimonio.audio : baseUrl + testimonio.audio"></audio>
              <button class="play-btn" @click="toggleAudio(index)" :class="{ playing: playingIndex === index }">
                <svg v-if="playingIndex !== index" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>
                <svg v-else viewBox="0 0 24 24" fill="currentColor"><path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"/></svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const testimonios = ref([]);
const baseUrl = import.meta.env.BASE_URL;

onMounted(async () => {
  try {
    const response = await fetch(baseUrl + 'data.json');
    const data = await response.json();
    testimonios.value = data.testimonios;
  } catch (error) {
    console.error('Error cargando testimonios:', error);
  }
});

const playingIndex = ref(null);

const toggleAudio = (index) => {
  const allAudios = document.querySelectorAll('audio');
  
  if (playingIndex.value === index) {
    const audio = document.getElementById('audio-' + index);
    audio.pause();
    playingIndex.value = null;
  } else {
    allAudios.forEach(a => a.pause());
    playingIndex.value = index;
    const audio = document.getElementById('audio-' + index);
    audio.play().catch(e => {
      console.error("Error al reproducir audio:", e);
      playingIndex.value = null;
      alert("Error al intentar reproducir el audio. Verifica que el archivo exista y el navegador lo soporte.");
    });
    
    audio.onended = () => {
      playingIndex.value = null;
    };
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

.testimonios-section {
  background-color: #fcfcfc;
  padding: 8rem 2rem;
  color: #111;
  font-family: 'Poppins', sans-serif;
}
.container { max-width: 1200px; margin: 0 auto; }
.section-title {
  text-align: center; font-size: 2.8rem; font-weight: 600; margin-bottom: 5rem; text-transform: uppercase; letter-spacing: 2px;
}
.section-title::after { content: ''; display: block; width: 60px; height: 3px; background-color: #D4AF37; margin: 1rem auto 0; }
.testimonios-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 3rem; }
.testimonio-card {
  background: #FFF; padding: 3rem 2.5rem; border-radius: 12px; box-shadow: 0 10px 30px rgba(0,0,0,0.04); transition: all 0.4s ease; border: 1px solid #eee; position: relative;
}
.testimonio-card:hover { transform: translateY(-10px); box-shadow: 0 15px 40px rgba(212,175,55,0.1); border-color: #D4AF37; }
.quote-icon { font-size: 5rem; color: #D4AF37; opacity: 0.2; position: absolute; top: 1rem; left: 2rem; font-family: serif; line-height: 1; }
.testimonio-text { font-size: 1.1rem; line-height: 1.7; color: #555; margin-bottom: 2.5rem; position: relative; z-index: 1; font-weight: 300; font-style: italic; }
.testimonio-footer { display: flex; justify-content: space-between; align-items: center; border-top: 1px solid #eee; padding-top: 1.5rem; }
.client-info h4 { margin: 0 0 0.2rem 0; font-size: 1.1rem; font-weight: 600; color: #111; }
.client-info span { font-size: 0.9rem; color: #888; font-weight: 300; }
.play-btn { width: 45px; height: 45px; border-radius: 50%; background-color: #FFF; border: 2px solid #D4AF37; color: #D4AF37; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: all 0.4s ease; box-shadow: 0 4px 10px rgba(212,175,55,0.2); outline: none; }
.play-btn svg { width: 20px; height: 20px; margin-left: 3px; }
.play-btn.playing svg { margin-left: 0; }
.play-btn:hover, .play-btn.playing { background-color: #D4AF37; color: #FFF; transform: scale(1.1); box-shadow: 0 6px 15px rgba(212,175,55,0.4); }
</style>
