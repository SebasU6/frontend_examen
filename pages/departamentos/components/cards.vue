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
  { title: 'Departamento Mirador', text: 'Dirección: Calle 17 de Calacoto No. 50, Edificio Mirador, Piso 3, Zona Calacoto, La Paz.      Descripción: Departamento de tres dormitorios, dos baños, cocina moderna y balcón con vista a la ciudad. Edificio con seguridad 24 horas.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.53d5d119630f1afb7a26388450bbb9c0253e4e6b.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.01bf1bbdf6c7ed5b8c83c14dc12f5e9ed1bf3099.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.2ed5e5c5e6244dd6479fff27adc6cb5af4c50482.jpg'] },
  { title: 'Residencia Altamira', text: 'Dirección: Avenida 6 de Agosto No. 123, Edificio Altamira, Piso 5, Zona San Jorge, La Paz.     Descripción: Departamento amplio de cuatro dormitorios, tres baños, sala de estar y comedor integrados, con acabados de lujo. Edificio con gimnasio y piscina.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside687x442.bc55244b776d6785d9a027ce79e46bf578e5b326.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.614a90f9da0b2fb22c9a5af9602b0cb451aff5b2.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.4dded519d49b1c38e1f2e957b92e6510ec3b3439.jpg'] },
  { title: 'Departamento Illimani', text: 'Dirección: Calle 21 No. 89, Edificio Illimani, Piso 7, Zona Achumani, La Paz.     Descripción: Departamento moderno de tres dormitorios, dos baños y una terraza con vista panorámica. Edificio con áreas comunes y parque infantil.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.e8c1d3295e5500f97e4bd0b5d6d68a3277fcbbbd.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.2cb1ec906a8a4677029e2471d70ea6700a0fb026.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.96a36705e508824ddbfcd127e16bb370775ea3f2.jpg'] },
  { title: 'Apartamento Colonial', text: 'Dirección: Avenida Busch No. 245, Edificio Colonial, Piso 2, Zona Miraflores, La Paz       Descripción: Departamento renovado con detalles coloniales, tres dormitorios, dos baños y un patio interno. Edificio céntrico y bien comunicado.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.f4de9027dce6fdade6395943e5c7d81a36f4c78f.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.f7276db766a45e808b4eea479aa250f8a0d4c02a.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.8897c26a34d65531a093317e6415436c09b2d6ca.jpg'] },
  { title: 'Departamento Bosques', text: 'Dirección: Calle 15 No. 78, Edificio Bosques, Piso 4, Zona Cota Cota, La Paz.       Descripción: Departamento de cuatro dormitorios, tres baños, cocina equipada y amplio balcón. Edificio con áreas verdes y seguridad privada.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.ffd3d17d6683d9bbf75bc1f171704497367f0725.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.d1a355bba4aa6ec32726c5ac26787cfb2c8881ab.jpg', ''] },
  { title: 'Residencia Panorama', text: 'Dirección: Calle Rosendo Gutiérrez No. 456, Edificio Panorama, Piso 10, Zona Sopocachi, La Paz.        Descripción: Departamento de lujo con cinco dormitorios, cinco baños, sala de estar con vista panorámica y acabados de alta calidad. Edificio con gimnasio y salón de eventos.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.646f797e0b054_rn_image_picker_lib_temp_fceeb0b8-c237-47d4-a514-4e3da65d83a4.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.646f798419855_rn_image_picker_lib_temp_1a53766c-1d9c-4bbb-887b-a02d4585766c.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.646f799fcdb1d_rn_image_picker_lib_temp_5e71e061-06a1-4caf-a3c7-69bc805e652c.jpg'] },
  { title: 'Residencia Alameda', text: 'Dirección: Avenida Montenegro No. 312, Edificio Alameda, Piso 3, Zona San Miguel, La Paz.          Descripción: Departamento de tres dormitorios, dos baños, cocina abierta y área de lavado. Edificio en fraccionamiento cerrado con seguridad.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.a487a9431ff48b69c103fc66a60b607b9413ba16.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.5cca9714f56e69a782b0dee5e0295eb01cbef672.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.f67733aadf0573747640883e699f6233f89055b8.jpg'] },
  { title: 'Departamento Central', text: 'Dirección: Avenida Camacho No. 678, Edificio Central, Piso 6, Zona Central, La Paz.             Descripción: Departamento con tres dormitorios, dos baños y un balcón. Edificio ubicado cerca de parques y servicios esenciales.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.5af3c23f1f781_received_10204903578905923.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.5af3c21830cdf_img_1524520063706.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.5af3c2590eb4b_img_1524519992446.jpg'] },
  { title: 'Apartamento Aurora', text: 'Dirección: Calle 12 de Obrajes No. 345, Edificio Aurora, Piso 2, Zona Obrajes, La Paz.            Descripción: Departamento de dos dormitorios, un baño, cocina integrada y pequeño balcón. Edificio con acceso fácil a comercios y transporte público.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.6f0bbd24b95dadd3e63fa1c37511472f81c279f4.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.b4bf041d00eead0d9349f38265949c703373fd2f.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.c8e112b631131efe7cbafa8933c3ab467399fefb.jpg'] },
])

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