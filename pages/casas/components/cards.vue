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
const router = useRouter()

import { ref } from 'vue';

const goTo = function(path){
router.push(path)
} 



// Simulated card data
const cards = ref([
  { title: 'Casa García', text: 'Dirección: Calle Los Olivos No. 15, Zona Sopocachi, La Paz.     Descripción: Propiedad unifamiliar de dos niveles con jardín frontal y trasero, tres recámaras, dos baños completos y garaje para un vehículo', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Residencia Las Palmas', text: 'Dirección: Avenida Arce No. 230, Zona San Jorge, La Paz.     Descripción: Vivienda moderna de cuatro recámaras, tres baños, amplia sala de estar, cocina equipada; ubicada en una zona tranquila y segura.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Villa Andina', text: 'Dirección: Calle 8 No. 12, Zona Calacoto, La Paz.     Descripción: Casa con diseño contemporáneo de tres recámaras, dos baños y una terraza con vista panorámica. Jardín amplio y garaje', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Casa Hernández', text: 'Dirección: Avenida 20 de Octubre No. 120, Zona Miraflores, La Paz.     Descripción: Casa renovada con detalles coloniales, cuatro recámaras, un patio central y acabados arquitectónicos originales.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Casa Los Pinos', text: 'Dirección: Calle 21 de Calacoto No. 45, Zona Achumani, La Paz.      Descripción: Propiedad de dos niveles con cuatro recámaras, tres baños completos, un jardín trasero grande y estacionamiento para dos vehículos.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Card Sánchez', text: 'Dirección: Calle 15 No. 78, Zona Obrajes, La Paz.      Descripción: Vivienda unifamiliar en fraccionamiento cerrado con seguridad, tres recámaras, dos baños completos, cocina moderna y patio trasero.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Residencia La Cima', text: 'Dirección: Calle Muñoz Reyes No. 89, Zona San Pedro, La Paz.      Descripción: Residencia de lujo con cinco recámaras, cinco baños, amplio jardín, alberca y vistas panorámicas de la ciudad.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Casa de la fuente', text: 'Dirección: Avenida del Libertador No. 50, Zona Central, La Paz.       Descripción: Casa tradicional con tres recámaras, patio con fuente y árboles frutales. Cerca de parques y servicios esenciales.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] },
  { title: 'Casa del Sol', text: 'Dirección: Calle 10 No. 34, Zona Cota Cota, La Paz.         Descripción: Casa de una planta con dos recámaras, un baño completo, cocina abierta y pequeño jardín. Ubicada en una zona accesible cerca de comercios y transporte público.', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'] }
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