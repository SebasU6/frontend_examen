<template>
    <v-container fluid>
        <cards></cards>
        <appbar></appbar>
        <footer-app></footer-app>
    </v-container>
</template>
<script setup>
import Cards from "./components/cards.vue"
import Appbar from "../index/components/appbar.vue"
import FooterApp from "../index/components/footer.vue"
</script>