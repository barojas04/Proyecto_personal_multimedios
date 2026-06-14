<template>
  <section id="flota" class="flota-section">
    <div class="container">
      <h2 class="section-title">Nuestra Flota</h2>
      <div class="grid-flota">
        <div class="gallery-card">
          <div class="image-wrapper">
            <img src="/imagen_carro.jpg" alt="Taxi Ejecutivo" class="gallery-img" />
            <div class="card-overlay">
              <span class="extra-info">Capacidad: 4 personas<br>Asientos de Cuero</span>
            </div>
          </div>
          <div class="card-content">
            <h3>Taxi de calidad</h3>
            <p>Unidad moderna, cómoda y climatizadas para su viaje personal o corporativo.</p>
          </div>
        </div>
        <div class="gallery-card">
          <div class="image-wrapper">
            <img src="/express.png" alt="Servicio Express" class="gallery-img" />
            <div class="card-overlay">
              <span class="extra-info">Entrega Express &lt; 30min<br>100% Seguro</span>
            </div>
          </div>
          <div class="card-content">
            <h3>Servicio Express</h3>
            <p>Mensajería rápida y segura. Entregamos sus documentos y paquetes a tiempo.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

.flota-section {
  background-color: #000;
  padding: 8rem 2rem;
  color: #FFF;
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.section-title {
  text-align: center;
  font-size: 2.8rem;
  font-weight: 600; 
  margin-bottom: 5rem;
  letter-spacing: 2px;
  text-transform: uppercase;
}
.section-title::after {
  content: '';
  display: block;
  width: 60px;
  height: 3px;
  background-color: #D4AF37;
  margin: 1rem auto 0;
}
.grid-flota {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 4rem;
}
.gallery-card {
  background-color: #0a0a0a;
  border-radius: 8px; 
  overflow: hidden;
  transition: all 0.4s ease;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}
.gallery-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(212, 175, 55, 0.15);
}
.image-wrapper {
  position: relative;
  width: 100%;
  height: 250px;
  overflow: hidden;
}
.gallery-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}
.gallery-card:hover .gallery-img {
  transform: scale(1.08);
}
.card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.4s ease;
}
.gallery-card:hover .card-overlay {
  opacity: 1;
}
.extra-info {
  color: #D4AF37;
  font-weight: 600;
  font-size: 1.1rem;
  text-align: center;
  transform: translateY(20px);
  transition: transform 0.4s ease;
  letter-spacing: 1px;
}
.gallery-card:hover .extra-info {
  transform: translateY(0);
}
.card-content {
  padding: 2.5rem;
  text-align: center;
  border-top: 2px solid #D4AF37;
}
.card-content h3 {
  font-size: 1.6rem;
  font-weight: 600;
  margin-bottom: 1rem;
  letter-spacing: 1px;
  color: #FFF;
}
.card-content p {
  color: #AAA;
  line-height: 1.6;
  font-weight: 300;
  margin: 0;
}
</style>
