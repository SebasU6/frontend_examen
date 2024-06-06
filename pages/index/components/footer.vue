<template>
  <v-footer
    class="wooden-color text-center d-flex flex-column custom-margin"
  >
    <div>
      <v-btn
        v-for="icon in icons"
        :key="icon"
        :icon="icon"
        class="mx-4"
        variant="text"
      ></v-btn>
    </div>

    <div class="pt-0">
      <h3>Contact Us</h3>
      <p>
        For inquiries or support, reach out to us through the following channels:
      </p>
      <p>
        <strong>Email:</strong> support@example.com <br>
        <strong>Phone:</strong> +1 (123) 456-7890 <br>
        <strong>Address:</strong> 123 Main Street, Anytown, AN 12345
      </p>
    </div>

    <v-divider></v-divider>

    <div>
      {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
    </div>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: [
      'mdi-facebook',
      'mdi-twitter',
      'mdi-linkedin',
      'mdi-instagram',
    ],
  }),
}
</script>

<style>
.wooden-color {
  background-color: #deb887 !important;
}

.custom-margin {
  margin-top: -2cm;
  margin-bottom: 0cm;
}

h3 {
  margin-bottom: 0.5em;
}

p {
  margin-bottom: 0.5em;
}
</style>
