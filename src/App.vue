<template>
  <div class="dashboard-container">
    <div class="welcome-card">
      <!-- Decoración visual superior -->
      <div class="card-badge">Vue.js 3 App</div>
      
      <!-- Título principal con gradiente -->
      <h1 class="main-title">¡Hola, <span class="highlight">{{ value }}</span>!</h1>
      
      <!-- Párrafo descriptivo -->
      <p class="description">
        Bienvenido a tu nuevo panel de control. Esta interfaz ha sido rediseñada 
        con CSS moderno para ofrecer una experiencia de usuario fluida y un aspecto premium.
      </p>

      <!-- Zona interactiva -->
      <div class="action-zone">
        <button @click="toggleLanguage" class="btn-primary">
          Cambiar Idioma
        </button>
        <p class="counter-text">Clicks realizados: <strong>{{ clickCount }}</strong></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      value: "Mundo",
      clickCount: 0
    };
  },
  methods: {
    toggleLanguage() {
      this.clickCount++;
      // Cambia dinámicamente entre Mundo (Español) y World (Inglés)
      this.value = this.value === "Mundo" ? "World" : "Mundo";
    }
  }
};
</script>

<style scoped>
/* Fondo general de la aplicación con un degradado sutil y moderno */
.dashboard-container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  padding: 20px;
}

/* Tarjeta contenedora estilo Neomorfismo / Glassmorphism suave */
.welcome-card {
  background: #ffffff;
  padding: 40px;
  border-radius: 24px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  max-width: 450px;
  width: 100%;
  text-align: center;
  transition: transform 0.3s ease;
}

.welcome-card:hover {
  transform: translateY(-5px);
}

/* Pequeña etiqueta superior */
.card-badge {
  display: inline-block;
  background-color: #e8f5e9;
  color: #2e7d32;
  font-size: 0.75rem;
  font-weight: 700;
  padding: 6px 16px;
  border-radius: 50px;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 20px;
}

/* Título con texto en degradado */
.main-title {
  color: #2c3e50;
  font-size: 2.5rem;
  margin: 0 0 15px 0;
  font-weight: 800;
}

.highlight {
  background: linear-gradient(135deg, #42b883 0%, #35495e 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Texto de descripción */
.description {
  color: #7f8c8d;
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 30px;
}

/* Sección del botón */
.action-zone {
  border-top: 1px solid #ecf0f1;
  padding-top: 25px;
}

/* Botón moderno con efectos de transición */
.btn-primary {
  background: linear-gradient(135deg, #42b883 0%, #35495e 100%);
  color: white;
  border: none;
  padding: 12px 28px;
  font-size: 1rem;
  font-weight: 600;
  border-radius: 12px;
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(66, 184, 131, 0.3);
  transition: all 0.2s ease;
}

.btn-primary:hover {
  box-shadow: 0 6px 20px rgba(66, 184, 131, 0.5);
  transform: scale(1.03);
}

.btn-primary:active {
  transform: scale(0.98);
}

/* Texto del contador */
.counter-text {
  margin-top: 15px;
  font-size: 0.85rem;
  color: #95a5a6;
}
</style>