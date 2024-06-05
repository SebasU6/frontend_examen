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
  { title: 'Departamento Mirador', text: 'Dirección: Calle 17 de Calacoto No. 50, Edificio Mirador, Piso 3, Zona Calacoto, La Paz.      Descripción: Departamento de tres dormitorios, dos baños, cocina moderna y balcón con vista a la ciudad. Edificio con seguridad 24 horas.', image: 'https://arq-3d.com/wp-content/uploads/2019/02/V1-1.jpg' },
  { title: 'Residencia Altamira', text: 'Dirección: Avenida 6 de Agosto No. 123, Edificio Altamira, Piso 5, Zona San Jorge, La Paz.     Descripción: Departamento amplio de cuatro dormitorios, tres baños, sala de estar y comedor integrados, con acabados de lujo. Edificio con gimnasio y piscina.', image: 'https://www.shutterstock.com/image-photo/modern-apartment-buildings-on-sunny-600nw-761409520.jpg' },
  { title: 'Departamento Illimani', text: 'Dirección: Calle 21 No. 89, Edificio Illimani, Piso 7, Zona Achumani, La Paz.     Descripción: Departamento moderno de tres dormitorios, dos baños y una terraza con vista panorámica. Edificio con áreas comunes y parque infantil.', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSMeTBUIS2H5V6scvlgw5KuQ_sBC5cARhJ5zQ&s' },
  { title: 'Apartamento Colonial', text: 'Dirección: Avenida Busch No. 245, Edificio Colonial, Piso 2, Zona Miraflores, La Paz       Descripción: Departamento renovado con detalles coloniales, tres dormitorios, dos baños y un patio interno. Edificio céntrico y bien comunicado.', image: 'https://proyectosdeviviendaenmonteria.com/wp-content/uploads/2023/09/fachada-praga.jpg' },
  { title: 'Departamento Bosques', text: 'Dirección: Calle 15 No. 78, Edificio Bosques, Piso 4, Zona Cota Cota, La Paz.       Descripción: Departamento de cuatro dormitorios, tres baños, cocina equipada y amplio balcón. Edificio con áreas verdes y seguridad privada.', image: 'https://static.fotocasa.es/images/promotion/2024/04/24/20415799/2932555.jpg?rule=web_412x257' },
  { title: 'Residencia Alameda', text: 'Dirección: Avenida Montenegro No. 312, Edificio Alameda, Piso 3, Zona San Miguel, La Paz.          Descripción: Departamento de tres dormitorios, dos baños, cocina abierta y área de lavado. Edificio en fraccionamiento cerrado con seguridad.', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTYF6LXiihacBpJjejBioyfam9dXnz9fOggA&s' },
  { title: 'Residencia Panorama', text: 'Dirección: Calle Rosendo Gutiérrez No. 456, Edificio Panorama, Piso 10, Zona Sopocachi, La Paz.        Descripción: Departamento de lujo con cinco dormitorios, cinco baños, sala de estar con vista panorámica y acabados de alta calidad. Edificio con gimnasio y salón de eventos.', image: 'https://x.cdrst.com/foto/hotel-sf/7e589/granderesp/departamentos-rondeau-by-lugar-exterior-f91568c.jpg' },
  { title: 'Departamento Central', text: 'Dirección: Avenida Camacho No. 678, Edificio Central, Piso 6, Zona Central, La Paz.             Descripción: Departamento con tres dormitorios, dos baños y un balcón. Edificio ubicado cerca de parques y servicios esenciales.', image: 'https://dynamic-media-cdn.tripadvisor.com/media/photo-o/2a/dd/06/59/exterior-view.jpg?w=700&h=-1&s=1' },
  { title: 'Apartamento Aurora', text: 'Dirección: Calle 12 de Obrajes No. 345, Edificio Aurora, Piso 2, Zona Obrajes, La Paz.            Descripción: Departamento de dos dormitorios, un baño, cocina integrada y pequeño balcón. Edificio con acceso fácil a comercios y transporte público.', image: 'https://thumbs.dreamstime.com/b/fachada-moderna-japonesa-de-departamentos-en-osaka-jap%C3%B3n-jp-abril-apartamentos-japoneses-el-181235537.jpg' }
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