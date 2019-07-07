<template>
  <v-container grid-list-lg>
    <v-layout justify-center row wrap>
      <v-flex v-for="(item,i) in newItems" :key="i" xs12 my-2>
        <v-card elevation="1" v-if="checkUniqle(item)">
          <v-card-title class = "title">{{item.name}}</v-card-title>
          <v-layout row wrap>
            <v-flex xs12 md4 px-3>
              <v-img src="https://cdn.vuetifyjs.com/images/cards/kitchen.png" :aspect-ratio="16/9"class="display-2 white--text" />
            </v-flex>
            <v-flex xs12 md8 px-3>
              {{item.label}}
            </v-flex>
          </v-layout>
          <v-layout justify-center align-center row pr-5 pb-2>
            <span class="title">Price: {{ item.price }}</span>
            <v-btn @click="addItem(item)">
              <v-icon>add</v-icon>
            </v-btn>
            <v-flex xs2>
              <v-layout class="title" justify-center>
                {{ showCount(item) }}
              </v-layout>
            </v-flex>
            <v-btn @click="removeItem(item)">
              <v-icon>remove</v-icon>
            </v-btn>
            <span class="title">Total price {{ showCount(item)*item.price }}</span>
          </v-layout>
          <v-card-actions>
            <v-btn
            icon
            absolute
            right
            large
            color="error"
            @click="deleteItem(i)"
            >
              <v-icon>delete</v-icon>
            </v-btn>
          </v-card-actions>


        </v-card>
      </v-flex>
      <v-layout justify-end class="display-1" pa-3>
        Total Price : {{ showTotal() }}
      </v-layout>
      <v-btn @click="someFunc()"></v-btn>
    </v-layout>
  </v-container>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  created(){
    this.cart = JSON.parse(localStorage.getItem("cart"));
    this.newItems = [];
    this.cart.forEach((cartItem)=>{
      this.items.filter(item => {
        item.id == cartItem.id ? this.newItems.push(item): null
      })
    })
  },
  data: () => ({
    cart:[],
    newItems: [],
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
    }),
  methods: {
    deleteItem(i){
      this.newItems.splice(i,1);
      this.cart.splice(i,1);
      const serialObj = JSON.stringify(this.cart)
      localStorage.setItem("cart",serialObj);
    },
    checkUniqle(item){
      if(this.cart.find((element, i ,arr)=> element.id == item.id)){
        return true;
      } else {
        return false;
      }
    },
    addItem(item){
      this.cart.find((element, i ,arr)=> element.id == item.id ? element.count++ : null);
      let serialObj = JSON.stringify(this.cart)
      localStorage.setItem("cart",serialObj);
    },
    removeItem(item){
      this.cart.find((element, i ,arr)=> element.id == item.id ? element.count>1 ? element.count-- : null  : null);
      let serialObj = JSON.stringify(this.cart)
      localStorage.setItem("cart",serialObj);
    },

    showCount(item){
      let count = this.cart.find((element, i ,arr)=> element.id == item.id ? element : null).count
      return count;
    },

    showTotal(){
      const reducer = (accumulator, currentValue) => accumulator + currentValue;
      const currentItems=[];
      this.cart.forEach((cartItem)=>{
        this.items.filter(item => {
          item.id == cartItem.id ? currentItems.push({"id":item.id, "totalPrice":item.price*cartItem.count}): null
        })
      })

      let vallue = currentItems.map((item)=> item.totalPrice).reduce(reducer)
      return vallue;
    }
  }
}
</script>
