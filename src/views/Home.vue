<template>
  <v-carousel
    :continuous="true"
    cycle
    interval="8000"
    :show-arrows="false"
    hide-delimiter-background
    vertical-delimiters
    delimiter-icon="mdi-eye"
    dark
    height="100%"
    class="grey darken-1 p-0 m-0"
  >
    <v-carousel-item
      v-for="(feature, index) in features"
      :key="index"
      transition="fade-transition"
      reverse-transition="fade-transition"
    >
      <v-sheet :color="colors[index]" height="100%" tile>
        <v-row class="fill-height" align="center" justify="center">
          <v-img :src="feature.artwork" width="200%" cover />
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "Home",
  components: {},

  data: () => ({
    colors: ["indigo", "warning", "pink darken-2"],
    features: [
      {
        artwork: require("../assets/releases/helloEP/cover.png"),
        linkPath: "",
      },
      { artwork: "", linkPath: "" },
      { artwork: "", linkPath: "" },
    ],
  }),
};
</script>
