<template>
  <v-app class="app">
    <v-navigation-drawer
      app
      absolute
      dark
      temporary
      max-height="95%"
      v-model="drawer"
      mobile-breakpoint="sm"
    >
      <router-link to="/home" class="text-decoration-none white--text d-flex">
        <v-img
          :src="menuTitle"
          contain
          aspect-ratio="1"
          alt="Metamind"
          height="50px"
          class="mx-3 my-2"
        />
      </router-link>
      <v-divider></v-divider>
      <v-list nav>
        <v-list-item-group v-model="selectedItem">
          <v-list-item v-for="(route, index) in routes" :key="index">
            <router-link
              :to="route.path"
              class="text-decoration-none white--text d-flex"
            >
              <v-list-item-icon>
                <v-icon color="purple accent-1" v-text="route.icon"></v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="route.label"></v-list-item-title>
              </v-list-item-content>
            </router-link>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      <v-footer padless absolute bottom>
        <v-card flat tile class="indigo lighten-1 white--text text-center">
          <v-card-text>
            <v-btn
              v-for="icon in footerIcons"
              :key="icon"
              class="mx-2 white--text"
              icon
            >
              <v-icon dense>
                {{ icon }}
              </v-icon>
            </v-btn>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-text class="text-caption">
            <v-icon x-small>mdi-copyright</v-icon>
            {{ new Date().getFullYear() }} — MetaMind Artistry Collective
          </v-card-text>
        </v-card>
      </v-footer>
    </v-navigation-drawer>
    <v-main fluid class="grey darken-3">
      <router-view />
      <v-fab-transition>
        <v-btn
          v-show="!hidden"
          class="purple accent-1 mb-12"
          fab
          dark
          right
          bottom
          absolute
          @click.stop="drawer = !drawer"
        >
          <v-icon>mdi-menu</v-icon>
        </v-btn>
      </v-fab-transition>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    selectedItem: 0,
    drawer: null,
    menuEye: require("./assets/metamind/eyepng.png"),
    menuTitle: require("./assets/metamind/metamind_BW.png"),
    footerIcons: ["mdi-facebook", "mdi-twitter", "mdi-instagram"],
    routes: [
      {
        label: "M u s i c",
        icon: "mdi-music-clef-bass",
        path: "/music",
      },
      {
        label: "N e w s",
        icon: "mdi-newspaper-variant-outline",
        path: "/news",
      },
      {
        label: "E v e n t s",
        icon: "mdi-calendar",
        path: "/events",
      },
      {
        label: "A r t i s t s",
        icon: "mdi-account-music-outline",
        path: "/artists",
      },
      {
        label: "A b o u t",
        icon: "mdi-information-outline",
        path: "/about",
      },
      {
        label: "C o n t a c t",
        icon: "mdi-email-outline",
        path: "/contact",
      },
    ],
  }),
};
</script>
