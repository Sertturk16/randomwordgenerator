<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">Random Word Generator</div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main style="background-color: #a5d6a7">
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
