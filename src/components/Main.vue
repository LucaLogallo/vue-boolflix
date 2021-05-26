<template>
  <div>

    <Movie 
    v-for="movie in movies" :key="movie.id"
    :movie="movie"
    />

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
  props:{
    /* gli passo la stringa che ho preso dall'header nell'app.vue in modo tale che poi posso fare la chiamata api con la query su questa stringa */
    search:String
  },
  data(){
    return{
      movies:[],
      /* richiesta api */
      api_url:'https://api.themoviedb.org/3/search/movie',
      api_key : '04262bfdc3da02e7444840a6bf3015b1',
      // ! error
      ricerca: this.search
      // ! /error
    }
  },
  mounted(){
    console.log(this.search)
    axios.get(this.api_url,{
      params:{
        api_key:this.api_key,
        // ! error
        query: this.ricerca,
        // ! /error
        language:"it-IT"
      }
    }
    )
    .then(res =>{
      this.movies = res.data.results
    })
    .catch(err =>{
      console.log(err)
    })
  }
}
</script>

<style>

</style>