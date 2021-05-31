<template>
  <div id="app">

   <!-- metto in ascolto l'header con la funzione che mi sono creato con emit e quindi con il @ nome della funzione andrò a richiamare una nuova funzione che mi farò nei methods -->
   <Header
   @startSearch="startSearch"
   />
   <h1 class="films" v-if="results.movie.length > 0">Film trovati</h1>
   <!-- al main passerò l'array che contiene sia l'array dei film che quello delle serie tv -->
   <Film
   v-if="results.movie.length > 0"
   id="FILM"
   :lista="results.movie" 
   type='movie'
   />

   <h1 class="tv" v-if="results.tv.length > 0">Serie Tv trovate</h1>
   <Tv
   v-if="results.tv.length > 0"
   :lista="results.tv" 
   type='tv'
   />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header';
import Film from './components/Film';
import Tv from './components/Tv';

export default {
  name: 'App',
  components: {
    Header,
    Film,
    Tv
  },
  data(){
    return{
      /* mi salvo il link per l'api in modo tale che nella chiamata axios passo le variabili in momdo da tenerla più pulita possibile */
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: '04262bfdc3da02e7444840a6bf3015b1',
      /* mi creo un oggetto che conterrà i due array uno per i film e l'altro per le serie tv che riempirò alla chiamata axios */
      results:{
        'movie':[],
        'tv':[]
      }
    }
  },
  methods:{
    /* gli passo la query alla chiamata della funzione così quando la richiamo le dico di cercarmi la query inserita */
    /* se gli passo anche il tipo in modo da poter dire se è un film oppure una serie tv non avrò problemi con la ricerca solo sulla serie tv oppure sui film */
    getAPI(query,type){
      axios.get(this.apiUrl+type,{
        params:{
        /* passo i parametri che mi servono nella chiamata */
        api_key: this.apiKey,
        query: query,
        language: 'it-IT'
      } 
      })
        .then(res =>{
          this.results[type] = res.data.results //relults[type] dove type cambia in base al type dato in ingresso nella getAPI quindi se faccio this.getAPI(obj.text,'movie'); result['movie'] mentre se faccio this.getAPI(obj.text,'tv'); allora result['tv']. Così avrò due array differenti. Uno che contiene i film e uno le serie tv. se uno dei due è vuoto allora vuol dire che stamperò quello pieno altrimenti se tutti e due sono pieni vuol dire che la ricerca sarò fatta su entrambi
          /* console.log(res.data); */  
          /*  console.log(res.data.results); */
          /* console.log(this.results[type]); */
        })
        .catch(err =>{
          console.log(err);
        })
    },
    startSearch(obj){ //funzione che ha in ingresso l'oggetto che contiene il text e il type della ricerca in base a quale bottone viene premuto tra film, serie tv ed entrambe
      /* console.log(obj) */ // ? log test
      this.resetResults();
      if(obj.type === 'all'){
        /* se è tutto mi fai due chiamate */
        this.getAPI(obj.text,'movie');
        this.getAPI(obj.text,'tv');
      }else{
        /* altrimenti prendo dall'oggetto il type selezionato */
        this.getAPI(obj.text,obj.type);
      }
    },
    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },
  },
  created(){
    /* this.getAPI('ciao','movie'); */ // ? log test
  }
}
</script>

<style lang="scss">
@import 'assets/scss/general.scss';

#app{
  background-color: #1b1b1b;
  height: 100%;
}
</style>
