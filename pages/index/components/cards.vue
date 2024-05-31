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
              <v-btn class="hover-button">Click me</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-parallax>
</template>

<script setup>
import { ref } from 'vue';

// Simulated card data
const cards = ref([
  { title: 'Card title 1', text: 'Content for card 1', images: ['https://arq-3d.com/wp-content/uploads/2019/02/V1-1.jpg', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyjapTlFyoSlz9V6YV7Fzov6resQvOQmwNmw&s', 'https://media.admagazine.com/photos/63b870f4147955e81067b4e7/16:9/w_320%2Cc_limit/_Q7I3359newnew_1.jpg'] },
  { title: 'Card title 2', text: 'Content for card 2', images: ['https://static.vecteezy.com/system/resources/previews/033/834/064/non_2x/exterior-of-a-modern-multi-story-apartment-building-facade-windows-and-balconies-photo.JPG', 'https://www.bienesonline.com/mexico/photos/departamento-en-venta-DEV3244581656942087-770.jpg', 'https://pics.nuroa.com/arriendo_hermoso_penthouse_con_vista_en_cumbaya_santa_lucia_alta_3080083713185010960.jpg'] },
  { title: 'Card title 3', text: 'Content for card 3', images: ['https://www.shutterstock.com/image-photo/modern-apartment-buildings-on-sunny-600nw-761409520.jpg', 'https://img.mitula.com/eyJidWNrZXQiOiJwcmQtbGlmdWxsY29ubmVjdC1iYWNrZW5kLWIyYi1pbWFnZXMiLCJrZXkiOiJwcm9wZXJ0aWVzL2U1MjNlNzUwLWYzNjYtNDQ5Ny04OWM0LTc4ZGFjNmQzODhlZi8yODUxY2Q0Yy01MmI4LTQ2MGUtOTBiNy1lYzNiMWYyZGUzOWEuanBnIiwiYnJhbmQiOiJNSVRVTEEiLCJlZGl0cyI6eyJyZXNpemUiOnsid2lkdGgiOjM4MCwiaGVpZ2h0IjoyMzAsImZpdCI6ImNvdmVyIn19fQ==', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT5af3rgRJOXNsYYsctfVCOB1A8sQQegQUgXg&s'] },
  { title: 'Card title 4', text: 'Content for card 4', images: ['https://static.vecteezy.com/system/resources/previews/028/854/847/non_2x/modern-apartment-building-exterior-with-green-plants-architectural-apartment-building-exterior-ai-generated-free-photo.jpg', 'https://bihui-1-departamento-la-paz.hotelmix.es/data/Photos/OriginalPhoto/11412/1141289/1141289473/Departamentos-Bihui-Apartment-La-Paz-Exterior.JPEG', 'https://www.ciudaris.com/blog/wp-content/uploads/destacado-ideas-maximizar-uso-terraza-departamento-nuevo-ciudaris.jpg'] },
  { title: 'Card title 5', text: 'Content for card 5', images: ['https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSMeTBUIS2H5V6scvlgw5KuQ_sBC5cARhJ5zQ&s', 'https://img10.naventcdn.com/avisos/18/01/43/61/62/47/360x266/1463555295.jpg?isFirstImage=true', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSJPXKx8QKAe2OXIlhYfj2YYVoWHJcgcqvhPw&s'] },
  { title: 'Card title 6', text: 'Content for card 6', images: ['https://static.vecteezy.com/system/resources/previews/013/463/468/non_2x/exterior-of-modern-red-brick-house-architectural-detail-of-close-up-on-windows-balconies-real-estate-residential-apartments-and-offices-living-apartments-or-office-building-architecture-photo.jpg', 'https://mir-s3-cdn-cf.behance.net/projects/404/95a45e197746583.Y3JvcCw0NDUyLDM0ODIsNTUxLDA.jpg', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTysdIEyUePF4Mcv9gNcxqEHWKxjeYX-xBALw&s'] },
  { title: 'Card title 7', text: 'Content for card 7', images: ['https://www.clarin.com/img/2021/03/24/n5TmM7HbA_720x0__1.jpg', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS74TuMOTRl5JXYBHqrYekQS46S1lWJTbWQaw&s', 'https://static.tokkobroker.com/pictures/108128938664988589107572551401621435910697011121165500558935346424117181415485.jpg'] },
  { title: 'Card title 8', text: 'Content for card 8', images: ['https://static.fotocasa.es/images/promotion/2024/04/24/20415799/2932555.jpg?rule=web_412x257', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSheoaAoNvqFPCXpeR6MIG98mVAiDfeS5M6SQ&s', 'https://e00-elmundo.uecdn.es/assets/multimedia/imagenes/2024/05/13/17155888834105.jpg'] },
  { title: 'Card title 9', text: 'Content for card 9', images: ['https://proyectosdeviviendaenmonteria.com/wp-content/uploads/2023/09/fachada-praga.jpg', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTWP6pASQ7zY3YI619oSOc1foM9YO7NXEnJDw&s', 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSN_qeGHcCALEASOd6eJJQ6a1orDpGu_NRIOw&s'] }
]);
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