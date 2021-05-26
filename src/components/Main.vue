<template>
  <div>

    <Movie />

  </div>
</template>

<script>
/* importo axios */
import axios from 'axios';

import Movie from '@/components/Movie'


export default {
  name:'Main',
  components:{
    Movie
  },
  data(){
    return{
      movies:[],
      /* richiesta api */
      api_url:'https://api.themoviedb.org/3/search/',
      query: 'query=',
      search: '',
      movie: 'movie?',
      tv:''
    }
  },
  created(){
   axios.get(this.api_url+)
  }
}
</script>

<style>

</style>