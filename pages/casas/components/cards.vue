<template>
  <v-parallax src="https://files.oaiusercontent.com/file-B6MNvK4JJJ6ep9oEGqNVf7ZM?se=2024-05-29T19%3A07%3A42Z&sp=r&sv=2023-11-03&sr=b&rscc=max-age%3D31536000%2C%20immutable&rscd=attachment%3B%20filename%3D65fd8454-766a-48a4-a2da-a9567cc8f0e0.webp&sig=Bg7JvbSUIyl668KBcPL2xNwlt7XFtZENQKHMVSP/dBg%3D">
    <v-container fluid>
      <v-row class="d-flex justify-center">
        <v-col
          v-for="(card, index) in cards"
          :key="index"
          cols="12"
          md="4"
          sm="12"
          xs="12"
          class="text-center"
        >
          <v-card class="mx-auto my-4 rounded-card hover-card">
            <v-carousel height="300px">
              <v-carousel-item
                v-for="(image, imgIndex) in card.images"
                :key="imgIndex"
                :src="image"
              ></v-carousel-item>
            </v-carousel>
            <v-card-title>{{ card.title }}</v-card-title>
            <v-card-text>{{ card.text }}</v-card-text>
            <v-card-actions class="justify-center">
              <v-btn @click="openDialog(card)" class="hover-button">Click me</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <v-dialog v-model="dialog" max-width="1000px">
      <v-card>
        <v-btn icon @click="dialog = false" class="close-button">
          <v-icon>mdi-close</v-icon>
        </v-btn>
        <v-card-text>
          <div class="popup-container">
            <div class="carousel-section">
              <v-carousel hide-delimiter-background>
                <v-carousel-item v-for="(image, imgIndex) in selectedCard.images" :key="imgIndex">
                  <v-img :src="image" height="300px"></v-img>
                </v-carousel-item>
              </v-carousel>
            </div>
            <div class="text-section">
              <div class="text-content">
                <h2>{{ selectedCard.title }}</h2>
                <p>{{ selectedCard.text }}</p>
              </div>
              <v-btn color="primary" @click="goTo('explore')">EXPLORAR</v-btn>
            </div>
          </div>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-parallax>
</template>

<script setup>
import { ref } from 'vue';

// Simulated card data
const cards = ref([
  { title: 'Card title 1', text: 'Content for card 1', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 2', text: 'Content for card 2', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 3', text: 'Content for card 3', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 4', text: 'Content for card 4', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 5', text: 'Content for card 5', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 6', text: 'Content for card 6', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 7', text: 'Content for card 7', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 8', text: 'Content for card 8', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card title 9', text: 'Content for card 9', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] }
]);

const dialog = ref(false);
const selectedCard = ref({});

const openDialog = (card) => {
  selectedCard.value = card;
  dialog.value = true;
};
</script>

<style scoped>
.popup-container {
  display: flex;
  flex-direction: row; /* Asegura que los elementos estén en fila */
  gap: 16px; /* Espacio entre las secciones */
}

.carousel-section {
  flex: 1;
}

.text-section {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center; /* Centra verticalmente el contenido */
  align-items: center; /* Centra el contenido horizontalmente */
}

.text-content {
  text-align: center; /* Centra el texto */
}

.explore-button {
  margin-top: 16px;
}

.v-dialog .v-card {
  overflow: hidden;
  display: flex;
  flex-direction: row; /* Asegura que los elementos estén en fila dentro del pop-up */
  position: relative;
}

.close-button {
  position: absolute;
  top: 8px;
  right: 8px;
}

.v-card {
  max-width: 1000px; /* Ajusta el ancho máximo del pop-up */
  transition: transform 0.3s ease; /* Transición para el efecto de agrandamiento */
  border-radius: 20px; /* Esquinas redondeadas */
}

.hover-card:hover {
  transform: scale(1.05); /* Agranda la tarjeta al pasar el ratón */
}

.rounded-card {
  border-radius: 20px; /* Ajusta el valor para esquinas más redondeadas */
}

.v-card-actions {
  display: flex;
  justify-content: center; /* Centra el botón horizontalmente */
}

.hover-button {
  transition: transform 0.3s ease; /* Transición para el efecto de agrandamiento */
}

.hover-button:hover {
  transform: scale(1.1); /* Agranda el botón al pasar el ratón */
}
</style>