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
  { title: 'Departamento Mirador', text: 'Dirección: Calle 17 de Calacoto No. 50, Edificio Mirador, Piso 3, Zona Calacoto, La Paz.      Descripción: Departamento de tres dormitorios, dos baños, cocina moderna y balcón con vista a la ciudad. Edificio con seguridad 24 horas.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.7d35a978a7d02ea07df8746558cb2997a262e017.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.a0da8d80e49c07dbbf744f1a34bcede7fd88c1b8.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.c250010f5f2dd4cdab0e517dab3563cc0cdedf38.jpg'] },
  { title: 'Residencia Altamira', text: 'Dirección: Avenida 6 de Agosto No. 123, Edificio Altamira, Piso 5, Zona San Jorge, La Paz.     Descripción: Departamento amplio de cuatro dormitorios, tres baños, sala de estar y comedor integrados, con acabados de lujo. Edificio con gimnasio y piscina.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.21d1e0ac11f90a79ffdc9346f62c20c2419a129c.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.15a61ce898937873167bdc09e8e75b674a14feb0.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.d0f589e3bf13b90eec1e3d3b0d757de3fa87944b.jpg'] },
  { title: 'Departamento Illimani', text: 'Dirección: Calle 21 No. 89, Edificio Illimani, Piso 7, Zona Achumani, La Paz.     Descripción: Departamento moderno de tres dormitorios, dos baños y una terraza con vista panorámica. Edificio con áreas comunes y parque infantil.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.e8c1d3295e5500f97e4bd0b5d6d68a3277fcbbbd.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.2cb1ec906a8a4677029e2471d70ea6700a0fb026.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.96a36705e508824ddbfcd127e16bb370775ea3f2.jpg'] },
  { title: 'Apartamento Colonial', text: 'Dirección: Avenida Busch No. 245, Edificio Colonial, Piso 2, Zona Miraflores, La Paz       Descripción: Departamento renovado con detalles coloniales, tres dormitorios, dos baños y un patio interno. Edificio céntrico y bien comunicado.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.ce01911adcd96e3cd24fae7d095b93895efaf5e9.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.32c406c8c3ea3afae60e49e899935066baf34f45.jpg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.5132c3d95eb077a7dd982c4237f708c5a1989e29.jpg'] },
  { title: 'Departamento Bosques', text: 'Dirección: Calle 15 No. 78, Edificio Bosques, Piso 4, Zona Cota Cota, La Paz.       Descripción: Departamento de cuatro dormitorios, tres baños, cocina equipada y amplio balcón. Edificio con áreas verdes y seguridad privada.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.e996b0e8da7329f6270545486f081f36e199617c.jpeg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.daf4a4e35fbc499f1e213e7f0209bc48f0b96cba.jpeg', 'https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.8bdbb1e6a99915a9c71f9bf11b72d259325e9394.jpeg'] },
  { title: 'Residencia Panorama', text: 'Dirección: Calle Rosendo Gutiérrez No. 456, Edificio Panorama, Piso 10, Zona Sopocachi, La Paz.        Descripción: Departamento de lujo con cinco dormitorios, cinco baños, sala de estar con vista panorámica y acabados de alta calidad. Edificio con gimnasio y salón de eventos.', images: ['https://cdn2.infocasas.com.uy/web/6321e0f1d62f2_infocdn__89ab873006d49954a8ae9f0dbc2fb02f31dff1','https://cdn2.infocasas.com.uy/web/6321e1015b327_infocdn__8a9b21907b2fdfcca9334c53e226e934869097','https://cdn2.infocasas.com.uy/web/6321e158cf122_infocdn__89b0117480419be39b82ec7151c84025863037'] },
  { title: 'Residencia Alameda', text: 'Dirección: Avenida Montenegro No. 312, Edificio Alameda, Piso 3, Zona San Miguel, La Paz.          Descripción: Departamento de tres dormitorios, dos baños, cocina abierta y área de lavado. Edificio en fraccionamiento cerrado con seguridad.', images: ['https://cdn2.infocasas.com.uy/web/605b41b403846_infocdn__8ad211bb493f2306ad78c988a1799616c8a123#HASTH','https://cdn2.infocasas.com.uy/web/605b41a4d0a77_infocdn__89a763e1d80606d7a6a99a9b7e85134da36961','https://cdn2.infocasas.com.uy/web/605b41af31fc4_infocdn__84dc93a1d896b698d94e674ccb51b2e2eb1ea1'] },
  { title: 'Departamento Central', text: 'Dirección: Avenida Camacho No. 678, Edificio Central, Piso 6, Zona Central, La Paz.             Descripción: Departamento con tres dormitorios, dos baños y un balcón. Edificio ubicado cerca de parques y servicios esenciales.', images: ['https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.d89e1bb506e46b516b1d6431de384110e1e8b175.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.24f624cd1ee99e3e7d5c723af2ab05a9b46dc420.jpg','https://cdn2.infocasas.com.uy/repo/img/th.outside500x1.37c2b5507d0144e11ec3c97379ac49c9e980c8ae.jpg'] },
  { title: 'Apartamento Aurora', text: 'Dirección: Calle 12 de Obrajes No. 345, Edificio Aurora, Piso 2, Zona Obrajes, La Paz.            Descripción: Departamento de dos dormitorios, un baño, cocina integrada y pequeño balcón. Edificio con acceso fácil a comercios y transporte público.', images: ['https://cdn2.infocasas.com.uy/web/5f809787cb309_infocdn__8c41418afec848a0c422f20004135311f6b491','https://cdn2.infocasas.com.uy/web/5f809782d274b_infocdn__8f157114d691b320172df7ed5af1cc744f3d01','https://cdn2.infocasas.com.uy/web/5f80977d21a0a_infocdn__88af116a53fe6b668acfa01d9168b2118624b1'] },
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