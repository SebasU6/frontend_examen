<template>
    <v-app-bar :elevation="0" >
      <v-app-bar-title text @click="goTo('/')">Index</v-app-bar-title>
  
       <v-btn text @click="goTo('/')">INICIO</v-btn>  

       <v-btn text @click="goTo('/casas')">CASAS</v-btn>
  
        <v-btn @click="goTo('/departamentos')">DEPARTAMENTOS</v-btn>
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