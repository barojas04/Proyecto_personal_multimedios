<template>
  <section id="contacto" class="contacto-section">
    <div class="container">
      <div class="contacto-wrapper">
        <div class="contacto-info">
          <h2 class="section-title left-align">Reserva tu Viaje</h2>
          <p class="contacto-desc">Viaja con seguridad, puntualidad y estilo. Llena el formulario o contáctanos directamente para coordinar tu próximo destino.</p>
          <ul class="info-list">
            <li><strong>📍 Base:</strong> Santa Cruz, Guanacaste</li>
            <li><strong>📞 Teléfono:</strong> +506 8888-8888</li>
            <li><strong>🕒 Horario:</strong> 24/7 Disponible</li>
          </ul>
        </div>
        <div class="contacto-form-container">
          <form @submit.prevent="enviarWhatsApp" class="contacto-form">
            <div class="form-group">
              <label for="nombre">Nombre Completo</label>
              <input type="text" id="nombre" v-model="form.nombre" required placeholder="Ej: Juan Pérez" />
            </div>
            <div class="form-group">
              <label for="telefono">Teléfono</label>
              <input type="tel" id="telefono" v-model="form.telefono" required placeholder="Ej: 8888 8888" />
            </div>
            <div class="form-group">
              <label for="destino">¿A dónde viaja?</label>
              <input type="text" id="destino" v-model="form.destino" required placeholder="Ej: Aeropuerto Liberia" />
            </div>
            <button type="submit" class="submit-btn">
              Reservar por WhatsApp
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue';

const form = reactive({
  nombre: '',
  telefono: '',
  destino: ''
});

const enviarWhatsApp = () => {
  const numero = '50688888888';
  const mensaje = `Hola Luis Rojas, me gustaría reservar un viaje.%0A%0A*Nombre:* ${form.nombre}%0A*Teléfono:* ${form.telefono}%0A*Destino:* ${form.destino}%0A%0A¡Quedo a la espera de confirmación!`;
  const url = `https://wa.me/${numero}?text=${mensaje}`;
  window.open(url, '_blank');
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

.contacto-section { background-color: #000; padding: 8rem 2rem; color: #FFF; font-family: 'Poppins', sans-serif; }
.container { max-width: 1200px; margin: 0 auto; }
.contacto-wrapper { display: flex; flex-wrap: wrap; gap: 4rem; justify-content: space-between; align-items: center; }
.contacto-info { flex: 1 1 400px; }
.section-title.left-align { text-align: left; font-size: 2.8rem; font-weight: 600; margin-bottom: 2rem; letter-spacing: 2px; text-transform: uppercase; }
.section-title.left-align::after { content: ''; display: block; width: 60px; height: 3px; background-color: #D4AF37; margin: 1rem 0 0; }
.contacto-desc { color: #AAA; font-size: 1.1rem; line-height: 1.8; margin-bottom: 3rem; font-weight: 300; }
.info-list { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 1.5rem; }
.info-list li { font-size: 1.1rem; color: #FFF; font-weight: 300; }
.info-list strong { color: #D4AF37; font-weight: 600; margin-right: 0.5rem; }
.contacto-form-container { flex: 1 1 500px; background: #0a0a0a; padding: 3rem; border-radius: 12px; border: 1px solid #222; box-shadow: 0 15px 40px rgba(0,0,0,0.5); }
.form-group { margin-bottom: 2rem; }
.form-group label { display: block; margin-bottom: 0.8rem; color: #DDD; font-size: 1rem; font-weight: 400; letter-spacing: 0.5px; }
.form-group input { width: 100%; padding: 16px; background-color: #111; border: 1px solid #333; border-radius: 8px; color: #FFF; font-size: 1.1rem; font-family: 'Poppins', sans-serif; transition: all 0.4s ease; box-sizing: border-box; }
.form-group input:focus { outline: none; border-color: #D4AF37; background-color: #1a1a1a; box-shadow: 0 0 10px rgba(212,175,55,0.2); }
.submit-btn { width: 100%; background-color: #D4AF37; color: #000; border: none; padding: 18px; font-size: 1.2rem; font-weight: 600; letter-spacing: 1px; border-radius: 8px; cursor: pointer; transition: all 0.4s ease; display: flex; align-items: center; justify-content: center; gap: 12px; text-transform: uppercase; box-shadow: 0 8px 20px rgba(212,175,55,0.3); }
.submit-btn:hover { background-color: #FFF; color: #000; transform: translateY(-3px); box-shadow: 0 12px 25px rgba(255,255,255,0.2); }
</style>
