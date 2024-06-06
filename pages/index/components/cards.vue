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
  { title: 'Casa Flores', text: 'Dirección: Calle Los Álamos No. 22, Zona Achumani, La Paz.        Descripción: Casa unifamiliar de dos niveles con jardín delantero y trasero, tres dormitorios, dos baños completos y garaje para dos vehículos.', images: ['https://cdn2.ultracasas.com/dyn/yastaimages/8991323b03c0f379994b9f10535401f6c8e000', 'https://cdn6.ultracasas.com/dyn/yastaimages/852c122018d84c6052d6ffb741f346811251f0', 'https://cdn6.ultracasas.com/dyn/yastaimages/8b7f00e132b155c27013ec97f48a99020e5582'], link: '/casas' },
  { title: 'Departamento Vista Verde', text: 'Dirección: Avenida 20 de Octubre No. 145, Edificio Vista Verde, Piso 4, Zona Miraflores, La Paz.                    Descripción: Departamento moderno de tres dormitorios, dos baños, cocina equipada y balcón con vista al parque. Edificio con gimnasio y seguridad 24 horas.', images: ['https://cdn1.ultracasas.com/dyn/yastaimages/8e9d89b8a43230e29823d8addc198124610621', 'https://cdn6.ultracasas.com/dyn/yastaimages/8c7a21697526b828c72cd3e28277398194d889', 'https://cdn8.ultracasas.com/dyn/yastaimages/89d9893804e149b9d840c39d9145a4be1a4a91'], link:'/departamentos'},
  { title: 'Casa del Prado', text: 'Dirección: Calle 12 de Obrajes No. 67, Zona Obrajes, La Paz.         Descripción: Casa amplia de tres niveles, cuatro dormitorios, tres baños, sala de estar, comedor, jardín grande y estacionamiento para dos autos.', images: ['https://cdn8.ultracasas.com/dyn/yastaimages/898289d9a1b264b088b3a6e82801aab17b3e31', 'https://cdn8.ultracasas.com/dyn/yastaimages/873a89590122b35338705db0a073afa0a32251', 'https://cdn8.ultracasas.com/dyn/yastaimages/8184996911b273d589029c554c3c9feb0f8b81'], link: '/casas' },
  { title: 'Residencia Altiplano', text: 'Dirección: Calle 15 No. 85, Edificio Altiplano, Piso 6, Zona Calacoto, La Paz.                 Descripción: Departamento de lujo con cuatro dormitorios, tres baños, sala de estar con grandes ventanales y vista panorámica. Edificio con piscina y salón de eventos.', images: ['https://cdn8.ultracasas.com/dyn/yastaimages/8fa49095a5823107a96aec59416d98a5ecfab1', 'https://cdn6.ultracasas.com/dyn/yastaimages/89c40043b156d0c3c03a4309491c894aabb5b1', 'https://cdn7.ultracasas.com/dyn/yastaimages/8d086083d1e610f1060cc50680a8611b37e271'], link: '/departamentos' },
  { title: 'Casa Encantada', text: 'Dirección: Avenida Ballivián No. 320, Zona Calacoto, La Paz.            Descripción: Casa familiar de dos plantas con cinco dormitorios, cuatro baños, amplia cocina, jardín y área de parrilla. Garaje para tres vehículos.', images: ['https://cdn8.ultracasas.com/dyn/yastaimages/87bc901393c79052b9bbaaa4c101435ad7c832', 'https://cdn8.ultracasas.com/dyn/yastaimages/85d78073b33720d6d8eda41576fc656a5e4b32', 'https://cdn7.ultracasas.com/dyn/yastaimages/83f660a333c7a014f6ec51ad6281ef9dae7552'], link: '/casas' },
  { title: 'Departamento La Paz', text: 'Dirección: Avenida Arce No. 123, Edificio La Paz, Piso 3, Zona San Jorge, La Paz.                     Descripción: Departamento moderno de tres dormitorios, dos baños, cocina abierta y balcón con vista a la ciudad. Edificio con gimnasio y seguridad las 24 horas.', images: ['https://cdn8.ultracasas.com/dyn/yastaimages/869a8518c0f889b098264dcfaefeae98af2191', 'https://cdn6.ultracasas.com/dyn/yastaimages/8911216e4133129191ff59b252b23928f04825', 'https://cdn8.ultracasas.com/dyn/yastaimages/87f99588a09849e2f97ce3f799da0f82664b01'], link: '/departamentos' },
  { title: 'Casa del Sol', text: 'Dirección: Calle 10 No. 90, Zona Cota Cota, La Paz.                   Descripción: Casa luminosa de una planta con tres dormitorios, dos baños, cocina moderna, jardín y garaje para un auto. Ubicada en una zona residencial tranquila.', images: ['https://cdn6.ultracasas.com/dyn/yastaimages/865022e953020e786574e38e32e627c3c02400', 'https://cdn7.ultracasas.com/dyn/yastaimages/841642c1340a204e41534471849616f3a06470', 'https://cdn7.ultracasas.com/dyn/yastaimages/8276425282e8723f27cf38ccf4c90723d08440'], link: '/casas' },
  { title: 'Residencia Central', text: 'Dirección: Calle 16 de Obrajes No. 67, Zona Obrajes, La Paz.       Descripción: Departamento de tres dormitorios, dos baños, cocina equipada y sala de estar amplia. Edificio céntrico cerca de oficinas y tiendas.', images: ['https://cdn7.ultracasas.com/dyn/yastaimages/89ae609265905029a6b9a96fe0c42492270762', 'https://cdn6.ultracasas.com/dyn/yastaimages/8eae32e433ae91c9ea398256b30750a0856260', 'https://cdn8.ultracasas.com/dyn/yastaimages/86d07905b9f9b7e5d77bc856093cd5c3596af1'], link: '/departamentos' },
  { title: 'Casa Bella Vista', text: 'Dirección: Calle 18 No. 45, Zona Bella Vista, La Paz.                      Descripción: Casa de dos niveles con cuatro dormitorios, tres baños, jardín grande, terraza y estacionamiento para dos vehículos. Zona residencial con hermosa vista a la ciudad.', images: ['https://cdn7.ultracasas.com/dyn/yastaimages/82694191d3569789264ec098f4e332f590b3b9', 'https://cdn7.ultracasas.com/dyn/yastaimages/8d1c51561a85887ed1575192f5b152c5b02309', 'https://cdn6.ultracasas.com/dyn/yastaimages/8319212f3ed37f6c3123f96f3209b1f5203349'], link: '/casas' }
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