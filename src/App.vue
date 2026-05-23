<template>
  <div class="world-cup-app">
    <!-- Encabezado Principal con Parallax/Gradiente -->
    <header class="hero-header">
      <div class="overlay"></div>
      <div class="header-content">
        <span class="badge-edition">Edición Histórica ✨</span>
        <h1>Copa Mundial de la FIFA 2026™</h1>
        <p>3 Países • 48 Selecciones • 104 Partidos</p>
      </div>
    </header>

    <!-- Sistema de Navegación por Pestañas (Tabs) con Animación -->
    <nav class="navigation-bar">
      <button 
        v-for="tab in tabs" 
        :key="tab.id"
        :class="['nav-btn', { active: currentTab === tab.id }]"
        @click="currentTab = tab.id"
      >
        <span class="icon">{{ tab.icon }}</span> {{ tab.name }}
      </button>
    </nav>

    <!-- Contenedor Principal con Transiciones de Entrada/Salida -->
    <main class="main-content">
      <transition name="fade-slide" mode="out-in">
        
        <!-- PESTAÑA 1: INICIO Y NOVEDADES -->
        <div v-if="currentTab === 'overview'" key="overview" class="tab-pane">
          <div class="welcome-grid">
            <div class="featured-card">
              <h3>🏆 Un Formato Revolucionario</h3>
              <p>Por primera vez en la historia, 48 selecciones competirán en la fase final. Los equipos se dividen en 12 grupos de 4 integrantes. Clasifican los dos mejores de cada grupo y los 8 mejores terceros a una nueva ronda inédita: los <strong>Dieciseisavos de Final</strong>.</p>
              <div class="status-tag">8 partidos necesarios para ser Campeón</div>
            </div>
            
            <div class="quick-facts">
              <div class="fact-box">
                <span class="fact-num">104</span>
                <span class="fact-label">Partidos Totales</span>
              </div>
              <div class="fact-box">
                <span class="fact-num">16</span>
                <span class="fact-label">Ciudades Sedes</span>
              </div>
              <div class="fact-box">
                <span class="fact-num">39</span>
                <span class="fact-label">Días de Magia</span>
              </div>
            </div>
          </div>
        </div>

        <!-- PESTAÑA 2: SEDES Y PAÍSES -->
        <div v-else-if="currentTab === 'venues'" key="venues" class="tab-pane">
          <h2 class="section-title">Distribución Geográfica del Torneo</h2>
          <div class="venues-grid">
            <div v-for="country in countries" :key="country.name" class="country-card">
              <div class="country-flag">{{ country.flag }}</div>
              <h3>{{ country.name }}</h3>
              <span class="match-count">{{ country.matches }} Partidos</span>
              <ul class="cities-list">
                <li v-for="city in country.cities" :key="city">{{ city }}</li>
              </ul>
            </div>
          </div>
        </div>

        <!-- PESTAÑA 3: GRUPOS DESTACADOS -->
        <div v-else-if="currentTab === 'groups'" key="groups" class="tab-pane">
          <h2 class="section-title">Anfitriones y Cabezas de Serie</h2>
          <div class="groups-grid">
            <div v-for="group in sampleGroups" :key="group.letter" class="group-card">
              <div class="group-header">Grupo {{ group.letter }}</div>
              <ul class="team-list">
                <li v-for="(team, index) in group.teams" :key="team" :style="{ animationDelay: index * 100 + 'ms' }" class="team-item">
                  <span class="position">{{ index + 1 }}</span> {{ team }}
                </li>
              </ul>
            </div>
          </div>
        </div>

      </transition>
    </main>

    <!-- Footer Corporativo -->
    <footer class="app-footer">
      <p>© 2026 - Diseñado con Vue.js para Ingeniería de Sistemas</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      currentTab: "overview",
      tabs: [
        { id: "overview", name: "Información", icon: "ℹ️" },
        { id: "venues", name: "Sedes y Estadios", icon: "🗺️" },
        { id: "groups", name: "Grupos", icon: "⚽" }
      ],
      countries: [
        {
          name: "Estados Unidos",
          flag: "🇺🇸",
          matches: 78,
          cities: ["Nueva York/NJ (Final)", "Dallas", "Los Ángeles", "Miami", "Atlanta", "Houston", "San Francisco", "Seattle", "Boston", "Filadelfia", "Kansas City"]
        },
        {
          name: "México",
          flag: "🇲🇽",
          matches: 13,
          cities: ["CDMX (Inaugural)", "Guadalajara", "Monterrey"]
        },
        {
          name: "Canadá",
          flag: "🇨🇦",
          matches: 13,
          cities: ["Vancouver", "Toronto"]
        }
      ],
      sampleGroups: [
        { letter: "A", teams: ["🇲🇽 México", "🇿🇦 Sudáfrica", "🇰🇷 Corea del Sur", "🇨🇿 Rep. Checa"] },
        { letter: "B", teams: ["🇨🇦 Canadá", "🇨🇭 Suiza", "🇶🇦 Qatar", "🇧🇦 Bosnia"] },
        { letter: "D", teams: ["🇺🇸 Estados Unidos", "🇵🇾 Paraguay", "🇦🇺 Australia", "🇹🇷 Turquía"] },
        { letter: "J", teams: ["🇦🇷 Argentina", "🇩🇿 Argelia", "🇦🇹 Austria", "🇯🇴 Jordania"] }
      ]
    };
  }
};
</script>

<style scoped>
/* --- CONFIGURACIÓN GENERAL Y ESTILOS BASE --- */
.world-cup-app {
  min-height: 100vh;
  background-color: #f4f7f6;
  font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* --- HERO HEADER CON EFECTO PREMIUM --- */
.hero-header {
  position: relative;
  background: linear-gradient(135deg, #0f2027 0%, #203a43 50%, #2c5364 100%);
  color: white;
  padding: 60px 20px;
  text-align: center;
  overflow: hidden;
}

.hero-header h1 {
  font-size: 2.8rem;
  margin: 10px 0;
  font-weight: 800;
  letter-spacing: -0.5px;
  text-shadow: 0 2px 10px rgba(0,0,0,0.3);
}

.hero-header p {
  font-size: 1.2rem;
  opacity: 0.9;
  margin: 0;
}

.badge-edition {
  background: rgba(255, 255, 255, 0.15);
  padding: 6px 16px;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* --- BARRA DE NAVEGACIÓN INTERACTIVA --- */
.navigation-bar {
  display: flex;
  justify-content: center;
  background: white;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
  sticky: top;
  z-index: 100;
  padding: 10px 0;
}

.nav-btn {
  background: transparent;
  border: none;
  padding: 12px 24px;
  margin: 0 8px;
  font-size: 1rem;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  border-radius: 12px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-btn:hover {
  background: #f1f5f9;
  color: #0f2027;
}

.nav-btn.active {
  background: #10b981;
  color: white;
  box-shadow: 0 4px 14px rgba(16, 185, 129, 0.3);
}

/* --- ÁREA DE CONTENIDO --- */
.main-content {
  max-width: 1100px;
  margin: 40px auto;
  padding: 0 20px;
  min-height: 400px;
}

.section-title {
  text-align: center;
  font-size: 1.8rem;
  margin-bottom: 30px;
  position: relative;
}

/* --- DISEÑO DE TARJETAS (PESTAÑA 1) --- */
.welcome-grid {
  display: grid;
  grid-template-columns: 2sfr 1fr;
  gap: 30px;
}

@media (max-width: 768px) {
  .welcome-grid { grid-template-columns: 1fr; }
}

.featured-card {
  background: white;
  padding: 35px;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.03);
  border-left: 6px solid #10b981;
}

.featured-card h3 { margin-top: 0; font-size: 1.5rem; }
.featured-card p { line-height: 1.7; color: #475569; }

.status-tag {
  display: inline-block;
  background: #ecfdf5;
  color: #065f46;
  padding: 8px 16px;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.9rem;
  margin-top: 15px;
}

.quick-facts {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.fact-box {
  background: white;
  padding: 20px;
  border-radius: 16px;
  text-align: center;
  box-shadow: 0 4px 15px rgba(0,0,0,0.02);
  transition: transform 0.3s ease;
}

.fact-box:hover { transform: translateY(-3px); }
.fact-num { display: block; font-size: 2rem; font-weight: 800; color: #1e3a8a; }
.fact-label { font-size: 0.9rem; color: #64748b; font-weight: 500; }

/* --- SEDES DE PAÍSES (PESTAÑA 2) --- */
.venues-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 25px;
}

.country-card {
  background: white;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.03);
  text-align: center;
}

.country-flag { font-size: 3rem; margin-bottom: 10px; }
.match-count {
  display: inline-block;
  background: #eff6ff;
  color: #1e40af;
  padding: 4px 12px;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 20px;
}

.cities-list {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: left;
  border-top: 1px solid #f1f5f9;
  padding-top: 15px;
}

.cities-list li {
  padding: 8px 0;
  color: #475569;
  font-size: 0.95rem;
  border-bottom: 1px dashed #f1f5f9;
}

/* --- TARJETAS DE GRUPOS (PESTAÑA 3) --- */
.groups-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}

.group-card {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0,0,0,0.02);
}

.group-header {
  background: #1e3a8a;
  color: white;
  padding: 12px;
  text-align: center;
  font-weight: 700;
  font-size: 1.1rem;
}

.team-list { list-style: none; padding: 10px 15px; margin: 0; }
.team-item {
  display: flex;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #f8fafc;
  font-weight: 500;
  animation: slideIn 0.4s ease forwards;
  opacity: 0;
}

.position {
  background: #f1f5f9;
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50px;
  font-size: 0.8rem;
  margin-right: 12px;
  color: #64748b;
}

/* --- ANIMACIONES DE VUE (TRANSITION) --- */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(15px);
}

.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-15px);
}

/* --- ANIMACIÓN CSS NATIVA PARA LAS LISTAS --- */
@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(-10px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* --- FOOTER --- */
.app-footer {
  text-align: center;
  padding: 30px;
  color: #94a3b8;
  font-size: 0.85rem;
  margin-top: 60px;
  border-top: 1px solid #e2e8f0;
}
</style>