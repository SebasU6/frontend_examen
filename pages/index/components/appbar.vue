<template>
    <v-app-bar :elevation="0" >
      <v-app-bar-title text @click="goTo('/')">Index</v-app-bar-title>
  
        <v-btn text @click="goTo('/products')">hola</v-btn>
  
        <v-btn @click="goTo('nosotros')">¿Quiénes somos?</v-btn>
  
        <v-btn @click="goTo('/busqueda_casas')">Búsqueda de casas</v-btn>
    </v-app-bar>
  </template>
  
  <script>
  export default {
    methods: {
      goTo(route){
      this.$router.push(route)
    }
  }
}
  </script>