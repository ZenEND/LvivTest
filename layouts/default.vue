<template>
  <v-app>
    <v-toolbar dark color="orange">
      <v-toolbar-title>
        Market Plase
      </v-toolbar-title>
      <v-spacer />
      <v-toolbar-items>
        <v-btn flat to="/">
          <v-icon>
            home
          </v-icon>
        </v-btn>
        <v-btn flat to="/cart">
          <v-icon>add_shopping_cart</v-icon>
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer app>
      <v-layout justify-center>
        <span>&copy; 2019</span>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
export default {}
</script>
