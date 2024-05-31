<template>
    <v-parallax src='https://castroseis.com/blog/wp-content/uploads/2019/09/colores-frios.jpg'>
        <v-container class="pa-5">
            <v-row class="justify-center align-center mb-5">
                <v-col cols="12" md="4" sm="12" xs="12" class="text-center bordered large-text"> 
                    Donde el deseo, la imaginacion y la realidad colicionan para ofrecerte todo lo que quisiste en un hogar donde puede quedarte tranquilo sabiendo que tomaste la mejor decision.
                </v-col>
                <v-col cols="12" md="4" sm="12" xs="12" class="d-flex justify-center bordered">
                    <v-img
                        class="square-image"
                        cover
                        src="https://moskito.mx/es/wp-content/uploads/sites/2/2023/12/modern-apartments-for-sale-in-tulum-090-departamento-1-recamara-plata-baja-recamara.jpg"
                    ></v-img>
                </v-col>
            </v-row>
            <v-row class="justify-center align-center mb-5">
                <v-col cols="12" md="4" sm="12" xs="12" class="d-flex justify-center bordered">
                    <v-img
                        class="square-image"
                        cover
                        src="https://casactualdiseno.com/wp-content/uploads/2021/07/jo_1-Photo.jpg"
                    ></v-img>
                </v-col>
                <v-col cols="12" md="4" sm="12" xs="12" class="text-center bordered large-text"> 
                    Encuentra tus acomodaciones que se adapten a ti para que puedar disfrutar de tu mejor momento ahora.
                </v-col>
            </v-row>
            <v-row class="justify-center align-center mb-5">
                <v-col cols="12" md="4" sm="12" xs="12" class="text-center bordered large-text"> 
                    Con nuestras selecciones y nuestras opciones al alcance de tus manos tenemos las llaves a tu proximo hogar.
                </v-col>
                <v-col cols="12" md="4" sm="12" xs="12" class="d-flex justify-center bordered">
                    <v-img
                        class="square-image"
                        cover
                        src="https://img.freepik.com/fotos-premium/fachada-edificio-apartamentos-moderno-exterior-nuevos-edificios-apartamentos_991208-963.jpg"
                    ></v-img>
                </v-col>
            </v-row>
        </v-container>
    </v-parallax>
</template>

<script setup>
</script>

<style scoped>
.square-image {
    width: 25vw;
    height: 25vw; 
    border: 2px solid white;
}
.text-center {
    text-align: center;
}
.bordered {
    border: 20px solid rgb(39, 39, 39);
    padding: 1px;
    background-color: rgba(255, 255, 255, 0.808); /* Optional: Adds a slight background to text for readability */
    border-radius: 8px;
}
.pa-5 {
    padding: 40px !important;
}
.mb-5 {
    margin-bottom: 40px !important;
}
.large-text {
    font-size: 1.5em;
    font-weight: bold;
}
</style>
