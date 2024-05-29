<template>
    <v-container fluid class="pa-0 ma-0">
        <hero></hero>
        <cards></cards>
        <seccion1></seccion1>
        <appbar></appbar>
        <footer-app></footer-app>
    </v-container>
</template>
<script setup>
import Hero from "./components/hero.vue"
import Cards from "./components/cards.vue"
import Seccion1 from "./components/seccion1.vue"
import Appbar from "./components/appbar.vue"
import FooterApp from "./components/footer.vue"
</script>