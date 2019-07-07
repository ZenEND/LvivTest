<template>
  <v-container grid-list-lg>
    <v-layout justify-center row wrap>
      <v-flex v-for="(item,i) in items" :key="i" xs12 md6 lg4>
        <v-hover>
          <v-card
            slot-scope="{ hover }"
            color="grey lighten-4"
          >
            <v-img
              :aspect-ratio="16/9"
              src="https://cdn.vuetifyjs.com/images/cards/kitchen.png"
            >
              <v-expand-transition>
                <div
                  v-if="hover"
                  class="d-flex transition-fast-in-fast-out orange darken-2 v-card--reveal display-3 white--text"
                  style="height: 100%;"
                >
                  {{item.price}}$
                </div>
              </v-expand-transition>
            </v-img>
            <v-card-text
              class="pt-4"
              style="position: relative;"
            >
              <v-btn
                absolute
                color="orange"
                class="white--text"
                @click="addItem(item)"
                fab
                large
                right
                top
              >
                <v-icon>add_shopping_cart</v-icon>
              </v-btn>
              <h3 class="display-1 font-weight-light orange--text mb-2"> {{item.name}}</h3>
              <div class="font-weight-light title mb-2">{{item.label}}</div>
            </v-card-text>
          </v-card>
        </v-hover>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  created(){
    this.cart = JSON.parse(localStorage.getItem("cart"));
  },
  data: () => ({
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
        "price":45
      }
      ],
      cart:[],
  }),
  methods: {
    addItem(item){
      if(!this.cart.find((element, i ,arr)=> element.id == item.id ? (
        element.count++
      ): (false))){
        this.cart.push({"id": item.id,"count":1});
      }
      let serialObj = JSON.stringify(this.cart)
      localStorage.setItem("cart",serialObj);
    },
  }
}
</script>

<style>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: .5;
  position: absolute;
  width: 100%;
}
</style>
