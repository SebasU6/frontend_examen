<template>
  <v-parallax src="https://files.oaiusercontent.com/file-oxiHp6AOSD8QP2GoIGZSvn2V?se=2024-05-29T19%3A31%3A45Z&sp=r&sv=2023-11-03&sr=b&rscc=max-age%3D31536000%2C%20immutable&rscd=attachment%3B%20filename%3Db70c62fc-f65c-4b41-b97b-efb770c727fb.webp&sig=TWk7AXLedHfOnnHASSgYAqjo5buuBZtVQEQeUzD79A8%3D">
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
  { title: 'Card title 1', text: 'Content for card 1', image: 'https://arq-3d.com/wp-content/uploads/2019/02/V1-1.jpg' },
  { title: 'Card title 2', text: 'Content for card 2', image: 'https://www.shutterstock.com/image-photo/modern-apartment-buildings-on-sunny-600nw-761409520.jpg' },
  { title: 'Card title 3', text: 'Content for card 3', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSMeTBUIS2H5V6scvlgw5KuQ_sBC5cARhJ5zQ&s' },
  { title: 'Card title 4', text: 'Content for card 4', image: 'https://proyectosdeviviendaenmonteria.com/wp-content/uploads/2023/09/fachada-praga.jpg' },
  { title: 'Card title 5', text: 'Content for card 5', image: 'https://static.fotocasa.es/images/promotion/2024/04/24/20415799/2932555.jpg?rule=web_412x257' },
  { title: 'Card title 6', text: 'Content for card 6', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTYF6LXiihacBpJjejBioyfam9dXnz9fOggA&s' },
  { title: 'Card title 7', text: 'Content for card 7', image: 'https://x.cdrst.com/foto/hotel-sf/7e589/granderesp/departamentos-rondeau-by-lugar-exterior-f91568c.jpg' },
  { title: 'Card title 8', text: 'Content for card 8', image: 'https://dynamic-media-cdn.tripadvisor.com/media/photo-o/2a/dd/06/59/exterior-view.jpg?w=700&h=-1&s=1' },
  { title: 'Card title 9', text: 'Content for card 9', image: 'https://thumbs.dreamstime.com/b/fachada-moderna-japonesa-de-departamentos-en-osaka-jap%C3%B3n-jp-abril-apartamentos-japoneses-el-181235537.jpg' }
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