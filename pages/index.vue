<template>
  <v-container grid-list-lg>
    <v-layout justify-center row wrap>
      <v-flex v-for="(item,i) in items" :key="i" py-4  xs8>
        <v-card>
          <v-card-title class="title">
            {{item.name}}
          </v-card-title>
          <v-card-text>
            <v-layout>
              <v-flex xs3>
                <v-img src="https://picsum.photos/1366/728?image=1" aspect-ratio="1"/>
              </v-flex>
              <p  class="subheading">
            {{item.label}}
              </p>
            </v-layout>
          </v-card-text>
          <v-card-actions>
            <v-btn icon color="primary" large absolute bottom right fab>
              <v-icon>
                add_shopping_cart
              </v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  data(){
    return{
      items:[
        {
          "id":1,
          "name":"article 1",
          "label":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut 	labore et dolore magna aliqua.",
          "price":25
        },
        {
          "id":2,
          "name":"article 2",
          "label":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          "price":35
        },
        {
          "id":3,
          "name":"article 3",
          "label":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          "price":45}
        ]

    }
  }
}
</script>
