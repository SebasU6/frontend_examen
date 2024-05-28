<template>
  <body>

<div class="hero-image">
<div class="hero-text">
  <h1 style="font-size:50px">Casas</h1>
  <p>Te otorgamos las llaves para abrir las puertas de tu sueño</p>
  <v-btn variant="tonal">Descubrelo</v-btn>
</div>
</div>

<p>Page Content..</p>

</body>
</template>
<style>
body, html {
height: 100%;
margin: 0;
font-family: Arial, Helvetica, sans-serif;
}

.hero-image {
background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("https://e1.pxfuel.com/desktop-wallpaper/942/966/desktop-wallpaper-houses-luxurious-house-luxury-home-wealthy-for-16-9-luxury-house.jpg");
height: 50%;
background-position: center;
background-repeat: no-repeat;
background-size: cover;
position: relative;
}

.hero-text {
text-align: center;
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
color: white;
}

.hero-text v-button {
border: none;
outline: 0;
display: inline-block;
padding: 10px 25px;
color: black;
background-color: #ddd;
text-align: center;
cursor: pointer;
}

.hero-text button:hover {
background-color: #2b85ce;
color: white;
}
</style>