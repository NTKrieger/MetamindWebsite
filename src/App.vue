<template>
  <v-app>
    <v-navigation-drawer app absolute height="100%" dark mobile-breakpoint="sm">
      <v-list class="indigo lighten-1">
        <v-list-item>
          <router-link
            to="/home"
            class="text-decoration-none white--text d-flex"
          >
            <v-list-item-content>
              <v-list-item-title class="font-weight-black">
                Metamind
              </v-list-item-title>
            </v-list-item-content>
          </router-link>
        </v-list-item>
      </v-list>
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
      <v-footer padless>
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
            {{ new Date().getFullYear() }} — Metamind Artistry Collective
          </v-card-text>
        </v-card>
      </v-footer>
    </v-navigation-drawer>
    <v-main>
      <v-container fluid>
        <router-view />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    selectedItem: 0,
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
