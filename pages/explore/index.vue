<template>
    <v-container fluid>
        <appbar></appbar>
        <div>
            <iframe 
                width="100%" 
                height="640" 
                frameborder="0" 
                allow="xr-spatial-tracking; gyroscope; accelerometer" 
                allowfullscreen 
                scrolling="no" 
                src="https://kuula.co/share/collection/7PcLg?logo=0&info=1&fs=1&vr=0&sd=1&thumbs=1">
            </iframe>
        </div>
    </v-container>
</template>

<script setup>
import Appbar from "../index/components/appbar.vue"
import kulaaviewer from "./components/kulaaviewer.vue";
</script>
