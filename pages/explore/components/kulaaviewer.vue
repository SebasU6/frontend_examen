<template>
  <div>
    <h1>Kuula Viewer</h1>
    <div v-if="error">{{ error }}</div>
    <div v-else-if="loading">Cargando...</div>
    <iframe v-else :src="kuulaUrl" width="100%" height="500px" frameborder="0" allowfullscreen></iframe>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'KuulaViewer',
  data() {
    return {
      loading: true,
      error: null,
      kuulaUrl: ''
    };
  },
  mounted() {
    this.fetchKuulaData();
  },
  methods: {
    async fetchKuulaData() {
      try {
        const response = await axios.get('https://kuula.co/share/5JJd9?logo=1&info=1&fs=1&vr=0&sd=1&thumbs=1'); // Reemplaza 'abc123' con tu ID de Kuula
        this.kuulaUrl = response.data.url; // Asegúrate de ajustar esto según la estructura de la respuesta de la API de Kuula
        this.loading = false;
      } catch (error) {
        this.error = 'Error al cargar el contenido de Kuula.';
        this.loading = false;
      }
    }
  }
};
</script>

<style scoped>
/* Estilos opcionales para tu componente */
</style>
