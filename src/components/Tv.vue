/* sui bottoni è stato messo il controllo che li fa apparire o scomparire se la lista (in questo caso di serie tv) esiste oppure no */

<template>
  <div class="contenitore">
    <!-- bottone per il precedente  -->
    <button class="prev"
    v-if="lista.length != 0"
    @click="prevCard()">
    <i class="fas fa-arrow-left"></i>
    </button>
    <!-- /bottone per il precedente  -->
  <div class="carosello d-inline-flex">

    <!-- card della "serie tv" -->
    <Card 
    :card = "lista[indexCard]"
    />
    <!-- /card della "serie tv" -->

    
  </div>

    <!-- bottone per il successivo -->
    <button class="next"
    v-if="lista.length != 0"
    @click="nextCard()">
    <i class="fas fa-arrow-right"></i>
    </button>
    <!-- /bottone per il successivo  -->


  <!-- pallini della lista di "serie tv" generati dinamicamente -->
  <div class="pallini"
    v-if="lista.length != 0"
  >
    <i
    @click="indexCard = index"
    
    v-for="index in lista" :key="index" class="active fas fa-circle">
    </i>
  </div>

  </div>


</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Tv',
  components:{
    Card
  },
  props:{
    type:String,
    lista:Array
  },
  data: function () {
    return{
      indexCard: 0,
    }
  },
  methods:{
    /* funzione che gestisce l'indice della card in modo tale da prendere quella precedente a quella mostrata ogni volta che si clicca il tasto prev viene richiamata */
    prevCard(){
      this.indexCard --;
      if(this.indexCard < 0) {
        this.indexCard = this.lista.length - 1;
      }
    },

    /* funzione che gestisce l'indice della card in modo tale da prendere quella successiva a quella mostrata ogni volta che si clicca il tasto next viene richiamata */
    nextCard(){
      this.indexCard ++;
      if(this.indexCard === this.lista.length){
        this.indexCard = 0;
        }
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';
/* regole per il contenitore delle carte */
.carosello{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* regole per il contenitore generale */
.contenitore{
  position: relative;
}

.prev,.next{
  color:#bbbbbb;
  position:absolute;
  top: 250px;
  background: none;
  border: none;
}
/* tasto precedente */
.prev{
  left: 10px;
}

/* tasto successivo */
.next{
  right: 10px;
}

.fa-arrow-right,.fa-arrow-left{
  font-size: 50px;
}

.pallini{
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom : -50px;
  display: inline;
  color: white;
}

.fas.fa-circle{
  display: inline;
  margin: 10px;
  color: rgb(171,6,15) ;
  cursor: pointer;
}

i.active{
  color: white;
}

</style>