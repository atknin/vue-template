<template>
  <v-app >
    <v-container class="grey lighten-5 text-center">
        <h1 class="muted mb-2"> Цена</h1>
        <v-row>
          <v-subheader>
            Наша цена, млн
          </v-subheader>
            <v-slider
              :max="122"
              :min="50"

              v-model="data.price_we"
              thumb-label="always"
            ></v-slider>
        </v-row>

        <v-row >
            <v-subheader>
              Цена ЭОС, млн
            </v-subheader>
            <v-slider
              v-model="data.price_eos"
              :max="122"
              :min="50"
              thumb-label="always"
            ></v-slider>
        </v-row>



        <hr class="ma-4" >
        <h1 class="muted mb-2"> Заявка</h1>
        <v-row>
          <v-subheader>
            Наша заяка, по 10 бальной шкале
          </v-subheader>
            <v-slider
              :max="10"
              :min="0"

              v-model="data.zayavka_we"
              thumb-label="always"
            ></v-slider>
        </v-row>

        <v-row >
            <v-subheader>
              Заяка ЭОС, по 10 бальной шкале
            </v-subheader>
            <v-slider
              v-model="data.zayavka_eos"
              :max="10"
              :min="0"
              thumb-label="always"
            ></v-slider>
        </v-row>




        <hr class="ma-4" >
        <h1 class="muted mb-2"> Люди</h1>
        <v-row>
          <v-subheader>
            Наша команада, человек
          </v-subheader>
            <v-slider
              :max="30"
              :min="0"

              v-model="data.people_we"
              thumb-label="always"
            ></v-slider>
        </v-row>

        <v-row >
            <v-subheader>
              Команда ЭОС, человек
            </v-subheader>
            <v-slider
              v-model="data.people_eos"
              :max="30"
              :min="0"
              thumb-label="always"
            ></v-slider>
        </v-row>


        <hr class="ma-4" >
        <h1 class="muted mb-2"> Контракты</h1>
        <v-row>
          <v-subheader>
            Наши, шт от 100 млн
          </v-subheader>
            <v-slider
              :max="3"
              :min="0"
              disabled
              v-model="data.kontrakt_we"
              thumb-label="always"
            ></v-slider>
        </v-row>

        <v-row >
            <v-subheader>
              ЭОС, шт от 100 млн
            </v-subheader>
            <v-slider
              v-model="data.kontrakt_eos"
              disabled
              :max="3"
              :min="0"
              thumb-label="always"
            ></v-slider>
        </v-row>


        <v-row >
            <v-subheader>
              Балы
            </v-subheader>
            <hr>
           <h1>Наши <span color='blue'>{{our_ball}} </span></h1>
           <h1>ЭОС <span color='red'>{{eos_ball}} </span></h1>
        </v-row>


    </v-container>
  </v-app>
</template>

<script>
import Vue from 'vue';


export default {

  name: 'app',

  data: () => ({
    data:{
      price_we: 90,
      price_eos: 120,
      zayavka_we: 10,
      zayavka_eos: 10,
      people_we: 7,
      people_eos: 30,
      kontrakt_we: 0,
      kontrakt_eos: 3,
    },
      max_work: 30
  
  }),
  computed: {
   
    eos_ball(){
      var price = Math.min(this.data.price_we,this.data.price_eos) /this.data.price_eos * 100

      var max = Math.max(this.data.people_we,this.data.people_eos)
      if (this.max_work > max) var kpred =  this.max_work 
      else  var kpred =  max
      var peop = this.data.people_eos / kpred * 100
 
      return  Math.round(price*0.6 + this.data.zayavka_eos + peop) + 50
    },
    our_ball(){
      var price = Math.min(this.data.price_we,this.data.price_eos) /this.data.price_we * 100

      var max = Math.max(this.data.people_we,this.data.people_eos)
      if (this.max_work > max) var kpred =  this.max_work 
      else  var kpred =  max
      var peop = this.data.people_we / kpred * 100

      return Math.round(price*0.6 + this.data.zayavka_we + peop)
    },
  },  
  mounted()
  {
    window.app = this.$refs.app;

    this.loadState();
  },

  methods:
  {
    
  }
}
</script>

<style>


</style>
