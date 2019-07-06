<template>
  <v-container grid-list-lg>
    <v-layout justify-center row wrap>
      <v-flex xs10 py-4>
        <v-card>
          <v-card-title class="title">
            Shopping Card
          </v-card-title>
          <v-card-text>
            <v-layout row wrap>
              <v-flex v-for="(item,i) in card" :key="i" xs12 my-2>
                <v-card elevation="10">
                  <v-btn color="error" @click="deleteItem(i)" icon fab absolute right>
                    <v-icon>delete</v-icon>
                  </v-btn>
                  <v-card-title class = "title">{{item.name}}</v-card-title>
                  <v-layout row pa-2>
                    <v-flex xs4>
                      <v-img src="https://picsum.photos/1366/728?image=3" class="display-2 white--text" />
                    </v-flex>
                    <v-flex>
                      {{item.label}}
                    </v-flex>
                  </v-layout>
                  <v-layout justify-end pr-5 pb-2>
                  <span class="title">Price: {{ item.price }}</span>
                  </v-layout>
                </v-card>
              </v-flex>
            </v-layout>
          </v-card-text>
          <v-card-actions>
            <v-layout justify-end class="display-1" pa-3>
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
        const reducer = (accumulator, currentValue) => accumulator + currentValue;
        return this.card.map(function(id){ return id.price}).reduce(reducer)
      }
    }
  }
}
</script>
