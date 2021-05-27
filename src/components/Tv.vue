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
  name: 'Tv',
  components:{
    Card
  },
  props:{
    lista:Array
  },
  data(){
    return{
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>