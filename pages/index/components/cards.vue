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
              <v-btn @click="goTo(card.link)" class="hover-button">Click me</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-parallax>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();

// Simulated card data
const cards = ref([
  { title: 'Card title 1', text: 'Content for card 1', images: ['https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/ac4257f1-2f82-40fc-8fed-a2e14c7c6400/d9m8qsw-890f42af-72c3-406f-a417-f78adc85f576.jpg/v1/fill/w_1024,h_747,q_75,strp/hora_de_aventura_casa_del_arbol_de_finn_y_jake_by_frankro_d9m8qsw-fullview.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9NzQ3IiwicGF0aCI6IlwvZlwvYWM0MjU3ZjEtMmY4Mi00MGZjLThmZWQtYTJlMTRjN2M2NDAwXC9kOW04cXN3LTg5MGY0MmFmLTcyYzMtNDA2Zi1hNDE3LWY3OGFkYzg1ZjU3Ni5qcGciLCJ3aWR0aCI6Ijw9MTAyNCJ9XV0sImF1ZCI6WyJ1cm46c2VydmljZTppbWFnZS5vcGVyYXRpb25zIl19.HXiD-s51SUI02b3b-gAEmiv3twtJJHjQaoHkyyjx1Lg', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRKCWc_S4jVnNws5qmZJy_jLqWxllFRiPOOog&s', 'https://i.pinimg.com/originals/e0/03/4a/e0034ad15363972efba94ef5e93a4a81.jpg'], link: '/casas' },
  { title: 'Card title 2', text: 'Content for card 2', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/departamentos' },
  { title: 'Card title 3', text: 'Content for card 3', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/casas' },
  { title: 'Card title 4', text: 'Content for card 4', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/departamentos' },
  { title: 'Card title 5', text: 'Content for card 5', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/casas' },
  { title: 'Card title 6', text: 'Content for card 6', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/departamentos' },
  { title: 'Card title 7', text: 'Content for card 7', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/casas' },
  { title: 'Card title 8', text: 'Content for card 8', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/departamentos' },
  { title: 'Card title 9', text: 'Content for card 9', images: ['https://via.placeholder.com/400x400', 'https://via.placeholder.com/400x400/ff0000', 'https://via.placeholder.com/400x400/00ff00'], link: '/casas' }
]);

const goTo = (link) => {
  router.push(link);
};
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