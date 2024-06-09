<template>
  <v-timeline>
    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://i.imgur.com/oOvNc7n.jpeg" alt="Sample Image" class="image" />
      </template>
      <div>
        <div class="name">Sebastian Uzqueda</div>
        <p class="description">
          CEO: Estudiante de la carrera de Negocios Digitales UCB - ePC<br>
        </p>
      </div>
    </v-timeline-item>

    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://i.imgur.com/zwF8OQ3.jpeg" alt="Bruno Image" class="image" />
      </template>
      <div>
        <div class="name">Bruno Coss</div>
        <p class="description">
          CEO: Estudiante de la carrera de Negocios y Ciencia de Datos UCB - ePC<br> 
        </p>
      </div>
    </v-timeline-item>

    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://i.imgur.com/Ao02j0l.jpeg" alt="Gabriel Image" class="image" />
      </template>
      <div>
        <div class="name">Gabriel Villarroel</div>
        <p class="description">
          CEO: Estudiante de la carrera de Negocios Digitales UCB - ePC<br>
        </p>
      </div>
    </v-timeline-item>

    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://i.imgur.com/66j1j3r.jpeg" alt="Miguel Angel Image" class="image" />
      </template>
      <div>
        <div class="name">Miguel Angel Montes de Oca</div>
        <p class="description">
          CEO: Estudiante de la carrera de Negocios Digitales UCB - ePC<br>
        </p>
      </div>
    </v-timeline-item>

    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://img.freepik.com/foto-gratis/mujer-joven-alegre-que-tiene-descanso-mientras-trabaja-casa-sentado-escritorio-frente-computadora-portatil-abierta_343059-852.jpg" alt="Sample Image" class="image" />
      </template>
      <div>
        <div class="name">Misión</div>
        <p class="description">
          "Nuestra misión es facilitar y acortar el tiempo de búsqueda de viviendas proporcionando una plataforma web y una aplicación intuitivas y eficaces. Nos comprometemos a ofrecer una experiencia personalizada y segura, ayudando a nuestros usuarios a encontrar la casa o departamento ideal con facilidad y confianza. A través de innovación constante y un enfoque en las necesidades de nuestros clientes, nos esforzamos por ser la solución más confiable para encontrar el hogar perfecto."
        </p>
      </div>
    </v-timeline-item>

    <v-timeline-item>
      <template v-slot:opposite>
        <img src="https://media.istockphoto.com/id/504481783/es/foto/dar-las-llaves-de-casa.jpg?s=612x612&w=0&k=20&c=j21NDOtk5hwkWCCm_iVTDMEFfZuyfxySJeali4Fsmm0=" alt="Sample Image" class="image" />
      </template>
      <div>
        <div class="name">Visión</div>
        <p class="description">
          "Ser la plataforma líder a nivel mundial en la búsqueda de viviendas, transformando el proceso de encontrar la casa de tus sueños en una experiencia simple, rápida y agradable, donde cada persona tenga las llaves para abrir la puerta de sus sueños."
        </p>
      </div>
    </v-timeline-item>
  </v-timeline>
</template>

<script setup></script>

<style>
.image {
  width: 350px;
  height: 350px;
  border: 5px solid #333; /* Border color and thickness */
  border-radius: 10px; /* Rounded corners */
}

.name {
  font-family: 'Roboto', sans-serif;
  font-size: 1.5rem;
  color: #333; /* Dark color for names */
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.description {
  font-family: 'Open Sans', sans-serif;
  font-size: 1rem;
  color: #666; /* Lighter color for descriptions */
  line-height: 1.5;
}
</style>
