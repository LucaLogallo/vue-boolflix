<template>
  <div class="container">
    <Card 
    :titolo = "titolo"
    type ='movie'
    />
    <Card 
    :titolo = "titolo"
    type ='tv'
    />
    
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Header',
  components:{
    Card
  },
  props:{
    /* mi passo results che è un array che contiene l'array di film e l'array di serie tv*/
    results: Object
  },
  data(){
    return{
      titolo:{
        'movie': 'Film trovati',
        'tv': 'Serie TV trovate'
      }
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>