<template>
  <v-parallax src="https://files.oaiusercontent.com/file-D02AIXFLo8jsuxxW49RjdGIh?se=2024-05-29T19%3A30%3A20Z&sp=r&sv=2023-11-03&sr=b&rscc=max-age%3D31536000%2C%20immutable&rscd=attachment%3B%20filename%3D6453865b-de2e-4505-b770-50133cea843b.webp&sig=EAQjd73bIbkzlOORfRK9YLq0xuxzVybmavGFB/VCx7o%3D">
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
            <v-img :src="card.image" class="white--text align-end" height="200px"></v-img>
            <v-card-title>{{ card.title }}</v-card-title>
            <v-card-text>{{ card.text }}</v-card-text>
            <v-card-actions class="justify-center">
              <v-btn class="hover-button" @click="redirect">Click me</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-parallax>
</template>

<script setup>
import { ref } from 'vue';

const router = useRouter()
// Simulated card data
const cards = ref([
  { title: 'Casa García', text: 'Dirección: Calle Los Olivos No. 15, Zona Sopocachi, La Paz.     Descripción: Propiedad unifamiliar de dos niveles con jardín frontal y trasero, tres recámaras, dos baños completos y garaje para un vehículo', image: 'https://imgix.cosentino.com/es/wp-content/uploads/2023/07/Lumire-70-Facade-MtWaverley-vic-1.jpg?auto=format%2Ccompress&ixlib=php-3.3.0' },
  { title: 'Residencia Las Palmas', text: 'Dirección: Avenida Arce No. 230, Zona San Jorge, La Paz.     Descripción: Vivienda moderna de cuatro recámaras, tres baños, amplia sala de estar, cocina equipada; ubicada en una zona tranquila y segura.', image: 'https://i.pinimg.com/564x/07/e9/ae/07e9ae27c9b9d4582cab297a63968db5.jpg' },
  { title: 'Villa Andina', text: 'Dirección: Calle 8 No. 12, Zona Calacoto, La Paz.     Descripción: Casa con diseño contemporáneo de tres recámaras, dos baños y una terraza con vista panorámica. Jardín amplio y garaje', image: 'https://yt3.googleusercontent.com/WrW6618RgyBqV55dpIU4or-IbY_suXoGI2fuje1ETuGyFDVXwmsvjtHB93K27yzaejNTmPrTNw=s900-c-k-c0x00ffffff-no-rj' },
  { title: 'Casa Hernández', text: 'Dirección: Avenida 20 de Octubre No. 120, Zona Miraflores, La Paz.     Descripción: Casa renovada con detalles coloniales, cuatro recámaras, un patio central y acabados arquitectónicos originales.', image: 'https://definicion.de/wp-content/uploads/2011/01/casa-2.jpg' },
  { title: 'Casa Los Pinos', text: 'Dirección: Calle 21 de Calacoto No. 45, Zona Achumani, La Paz.      Descripción: Propiedad de dos niveles con cuatro recámaras, tres baños completos, un jardín trasero grande y estacionamiento para dos vehículos.', image: 'https://images.adsttc.com/media/images/623c/4fa0/3e4b/3145/3000/001b/newsletter/_d_ambrosio_07._copy.jpg?1648119692' },
  { title: 'Card Sánchez', text: 'Dirección: Calle 15 No. 78, Zona Obrajes, La Paz.      Descripción: Vivienda unifamiliar en fraccionamiento cerrado con seguridad, tres recámaras, dos baños completos, cocina moderna y patio trasero.', image: 'https://hips.hearstapps.com/hmg-prod/images/casa-caracol-1526458370.jpeg?crop=0.669xw:1.00xh;0.331xw,0&resize=640:*' },
  { title: 'Residencia La Cima', text: 'Dirección: Calle Muñoz Reyes No. 89, Zona San Pedro, La Paz.      Descripción: Residencia de lujo con cinco recámaras, cinco baños, amplio jardín, alberca y vistas panorámicas de la ciudad.', image: 'https://www.rocketmortgage.com/resources-cmsassets/RocketMortgage.com/Article_Images/Large_Images/Types%20Of%20Homes/Stock-Gray-Ranch-Style-Home-AdobeStock_279953994-copy.jpeg' },
  { title: 'Casa de la fuente', text: 'Dirección: Avenida del Libertador No. 50, Zona Central, La Paz.       Descripción: Casa tradicional con tres recámaras, patio con fuente y árboles frutales. Cerca de parques y servicios esenciales.', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQDFvZImwpOrpfyhuRkAPHIHIP6UFxMheWb0Q&s' },
  { title: 'Casa del Sol', text: 'Dirección: Calle 10 No. 34, Zona Cota Cota, La Paz.         Descripción: Casa de una planta con dos recámaras, un baño completo, cocina abierta y pequeño jardín. Ubicada en una zona accesible cerca de comercios y transporte público.', image: 'https://arquitectopablorestrepo.com/wp-content/uploads/2024/02/Diseno-casa-campestre-La-Ladera-2-400x300.jpg' }
]);

const redirect = function() {
  router.push("/explore")
}

</script>

<style scoped>
.v-card {
  max-width: 400px;
  transition: transform 0.3s ease; /* Transición para el efecto de agrandamiento */
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