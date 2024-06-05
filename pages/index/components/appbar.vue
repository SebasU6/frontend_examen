<template>
  <v-container>
    <v-app-bar :elevation="0" class="app-bar">
      <v-app-bar-title class="title-text" @click="goTo('/')">3HOUSED</v-app-bar-title>

      <v-spacer></v-spacer> <!-- Añadir un espaciador para empujar los botones a la derecha -->

      <v-btn text class="button-text fixed-width mx-3" @mouseover="hoverButton('inicio')" @mouseleave="leaveButton('inicio')" @click="goTo('/')">
        <v-icon v-if="hoveredButton === 'inicio'" class="icon">mdi-home</v-icon>
        <span v-else>INICIO</span>
      </v-btn>

      <v-btn text class="button-text fixed-width mx-6" @mouseover="hoverButton('casas')" @mouseleave="leaveButton('casas')" @click="goTo('/casas')">
        <v-icon v-if="hoveredButton === 'casas'" class="icon">mdi-home-city</v-icon>
        <span v-else>CASAS</span>
      </v-btn>

      <v-btn text class="button-text fixed-width mx-6" @mouseover="hoverButton('departamentos')" @mouseleave="leaveButton('departamentos')" @click="goTo('/departamentos')">
        <v-icon v-if="hoveredButton === 'departamentos'" class="icon">mdi-office-building</v-icon>
        <span v-else>DEPARTAMENTOS</span>
      </v-btn>

      <v-btn text class="button-text fixed-width mx-6" @mouseover="hoverButton('nosotros')" @mouseleave="leaveButton('nosotros')" @click="goTo('/nosotros')">
        <v-icon v-if="hoveredButton === 'nosotros'" class="icon">mdi-account-group</v-icon>
        <span v-else>NOSOTROS</span>
      </v-btn>
    </v-app-bar>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      hoveredButton: null
    };
  },
  methods: {
    goTo(route) {
      this.$router.push(route);
    },
    hoverButton(button) {
      this.hoveredButton = button;
    },
    leaveButton(button) {
      if (this.hoveredButton === button) {
        this.hoveredButton = null;
      }
    }
  }
};
</script>

<style scoped>
.app-bar {
  background-color: #f5f5dc; /* Color blanco medio crema */
  color: rgb(0, 0, 0); /* Color del texto dentro de la barra de aplicación */
}

.title-text {
  font-size: 24px; /* Tamaño del texto del título */
  font-weight: bold; /* Negrita para el título */
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3); /* Efecto 3D */
}

.button-text {
  font-size: 18px; /* Tamaño del texto de los botones */
  font-weight: bold; /* Negrita para los botones */
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3); /* Efecto 3D */
  transition: transform 0.3s ease; /* Transición para el efecto de agrandamiento */
}

.button-text:hover {
  transform: scale(1.1); /* Agranda el botón al pasar el ratón */
}

.fixed-width {
  width: 120px; /* Establece un ancho fijo suficiente para ambos, el texto y el icono */
  display: flex;
  justify-content: center;
}

.icon {
  font-size: 24px; /* Ajusta el tamaño del icono */
}

.mx-3 {
  margin-left: 12px;
  margin-right: 12px; /* Añade un poco de espacio a ambos lados del botón INICIO */
}

.mx-6 {
  margin-left: 24px;
  margin-right: 24px; /* Añade más espacio a ambos lados de los otros botones */
}
</style>