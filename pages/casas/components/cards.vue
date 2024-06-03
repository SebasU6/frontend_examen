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
  { title: 'Casa García', text: 'Dirección: Calle Los Olivos No. 15, Zona Sopocachi, La Paz', image: 'https://imgix.cosentino.com/es/wp-content/uploads/2023/07/Lumire-70-Facade-MtWaverley-vic-1.jpg?auto=format%2Ccompress&ixlib=php-3.3.0' },
  { title: 'Residencia Las Palmas', text: 'Dirección: Avenida Arce No. 230, Zona San Jorge, La Paz', image: 'https://i.pinimg.com/564x/07/e9/ae/07e9ae27c9b9d4582cab297a63968db5.jpg' },
  { title: 'Card title 3', text: 'Content for card 3', image: 'https://yt3.googleusercontent.com/WrW6618RgyBqV55dpIU4or-IbY_suXoGI2fuje1ETuGyFDVXwmsvjtHB93K27yzaejNTmPrTNw=s900-c-k-c0x00ffffff-no-rj' },
  { title: 'Card title 4', text: 'Content for card 4', image: 'https://definicion.de/wp-content/uploads/2011/01/casa-2.jpg' },
  { title: 'Card title 5', text: 'Content for card 5', image: 'https://images.adsttc.com/media/images/623c/4fa0/3e4b/3145/3000/001b/newsletter/_d_ambrosio_07._copy.jpg?1648119692' },
  { title: 'Card title 6', text: 'Content for card 6', image: 'https://hips.hearstapps.com/hmg-prod/images/casa-caracol-1526458370.jpeg?crop=0.669xw:1.00xh;0.331xw,0&resize=640:*' },
  { title: 'Card title 7', text: 'Content for card 7', image: 'https://www.rocketmortgage.com/resources-cmsassets/RocketMortgage.com/Article_Images/Large_Images/Types%20Of%20Homes/Stock-Gray-Ranch-Style-Home-AdobeStock_279953994-copy.jpeg' },
  { title: 'Card title 8', text: 'Content for card 8', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQDFvZImwpOrpfyhuRkAPHIHIP6UFxMheWb0Q&s' },
  { title: 'Card title 9', text: 'Content for card 9', image: 'https://arquitectopablorestrepo.com/wp-content/uploads/2024/02/Diseno-casa-campestre-La-Ladera-2-400x300.jpg' }
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