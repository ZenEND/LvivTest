<template>
  <v-app light>
    <v-toolbar dark color="primary">
      <v-toolbar-title>
        Интернет магазин
      </v-toolbar-title>
      <v-spacer />
      <v-toolbar-items>
        <v-btn flat to="/">
          <v-icon>
            home
          </v-icon>
          Home Page
        </v-btn>
        <v-btn flat to="/card">
          <v-icon>delete</v-icon>
          Shopping Card
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      app
    >
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      items: [
        {
          icon: 'apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'bubble_chart',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
