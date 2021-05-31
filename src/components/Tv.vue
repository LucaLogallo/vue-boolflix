<template>
  <div class="contenitore">
    <button class="prev"
    v-if="lista.length != 0"
    @click="prevCard()">
    <i class="fas fa-arrow-left"></i>
    </button>
  <div class="carosello d-inline-flex">

    <Card 
    :card = "lista[indexCard]"
    />
    
  </div>
    <button class="next"
    v-if="lista.length != 0"
    @click="nextCard">
    <i class="fas fa-arrow-right"></i>
    </button>

  <div class="pallini"
    v-if="lista.length != 0"
  >
    <i
    :class="index === indexCard ? 'active' : null"
    v-for="index in lista" :key="index" class="fas fa-circle"></i>
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
    prevCard(){
      this.indexCard --;
      if(this.indexCard < 0) {
        this.indexCard = this.lista.length - 1;
      }
    },
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

.carosello{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

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
.prev{
  left: 10px;
}
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
}

i.active{
  color: white;
}

</style>