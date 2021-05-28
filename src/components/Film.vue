<template>
  <div class="container d-inline-flex">

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
  data: function () {
    return{
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>