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
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Film',
  components:{
    Card
  },
  props:{
    type:String,
    lista:Array
  },
  data: function () {
    return{
      indexCard: 0
    }
  },
  methods:{
    prevCard(){
      this.indexCard --;
      if(this.indexCard < 0) {
        this.indexCard = this.lista.length - 1;
      }
      console.log(this.indexCard)
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
/
<style lang="scss" scoped>
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
</style> 