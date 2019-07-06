<template>
  <v-container grid-list-lg>
    <v-layout justify-center row wrap>
      <v-flex py-4  xs10>
        <v-card>
          <v-card-title class="title">
            Shopping Card
          </v-card-title>
          <v-card-text>
            <v-layout row wrap>
              <v-flex v-for="(item,i) in card" :key="i" xs12 pa-1>
                <v-card flat>
                  <v-btn color="error" @click="deleteItem(i)" icon fab absolute right>
                    <v-icon>delete</v-icon>
                  </v-btn>
                  <v-flex xs12>
                    <v-img src="https://picsum.photos/1366/728?image=3" class="display-2 white--text">
                    {{item.name}}
                    </v-img>
                    <span class="title">Price: {{ item.price }}</span>
                  </v-flex>
                </v-card>
              </v-flex>
            </v-layout>
          </v-card-text>
          <v-card-actions>
            <v-layout justify-end class="display-1">
              Total Price : {{ showTotal() }}
            </v-layout>
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
  created(){
    this.card = JSON.parse(localStorage.getItem("card"));
  },
  data(){
    return{
      card:[],
      deleteItem(i){
        this.card.splice(i,1);
        var serialObj = JSON.stringify(this.card)
        localStorage.setItem("card",serialObj);
      },
      showTotal(){
        console.log(this.card)
        const reducer = (accumulator, currentValue) => accumulator + currentValue;
        console.log(this.card.reduce(reducer))
      }
    }
  }
}
</script>
