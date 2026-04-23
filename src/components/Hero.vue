<template>
  <section id="inicio" class="hero">
    <!-- Contenedor del video de fondo -->
    <div class="video-container">
      <video autoplay loop muted playsinline class="background-video">
        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4" />
        Tu navegador no soporta videos HTML5.
      </video>
    </div>
    
    <!-- Capa semitransparente oscura para mejorar legibilidad del texto -->
    <div class="overlay"></div>

    <!-- Contenido principal y texto de impacto -->
    <div class="hero-content">
      <h1 class="title">Tu viaje seguro, rápido y confiable</h1>
      <p class="subtitle">Servicio de transporte y mensajería 24/7 en Santa Cruz, Guanacaste.</p>
      <button class="cta-button" @click="solicitarViaje">Solicitar Viaje</button>
    </div>
  </section>
</template>

<script setup>
// Lógica para el botón de llamada a la acción
const solicitarViaje = () => {
  console.log("Iniciando solicitud de viaje...");
  // Aquí podríamos en el futuro abrir un modal de WhatsApp o redirigir a una vista de contacto
  alert("¡Pronto podrás solicitar tu viaje por aquí!");
};
</script>

<style scoped>
/* Contenedor principal de la sección Hero */
.hero {
  position: relative;
  width: 100%;
  height: 100vh; /* Ocupa toda la altura de la ventana del navegador */
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

/* Configuración del contenedor del video */
.video-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -2; /* Se ubica en el fondo de todo */
}

/* El video cubre todo el espacio disponible */
.background-video {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Evita que el video se estire o deforme */
}

/* Filtro oscuro para resaltar el texto blanco */
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6); 
  z-index: -1; 
}

/* Agrupación de los textos y botones */
.hero-content {
  text-align: center;
  color: #ffffff;
  z-index: 1; /* Se sitúa frente al overlay y el video */
  padding: 0 20px;
  max-width: 800px;
}

/* Título principal atractivo */
.title {
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5); /* Sombra para mejor lectura */
}

/* Subtítulo descriptivo */
.subtitle {
  font-size: 1.5rem;
  margin-bottom: 2.5rem;
  line-height: 1.5;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5);
}

/* Botón llamativo (Call to Action) */
.cta-button {
  background-color: #f39c12; /* Color distintivo del servicio */
  color: #1a1a1a;
  border: none;
  padding: 15px 40px;
  font-size: 1.2rem;
  font-weight: bold;
  border-radius: 8px; /* Bordes redondeados más modernos */
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(243, 156, 18, 0.4); /* Resplandor sutil */
}

/* Interacción al pasar el mouse por el botón */
.cta-button:hover {
  background-color: #e67e22; /* Se oscurece ligeramente */
  transform: translateY(-3px); /* Efecto de elevación */
  box-shadow: 0 6px 20px rgba(243, 156, 18, 0.6);
}

.cta-button:active {
  transform: translateY(0); /* Vuelve a su lugar al hacer clic */
}
</style>
