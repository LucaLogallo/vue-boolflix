<template>
  <div class="container">
    <Card 
    v-for="card in lista" 
    :key="card.id"
    :card = "card"
    />
    
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
  data(){
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>