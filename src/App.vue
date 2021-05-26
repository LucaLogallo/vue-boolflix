<template>
  <div id="app">
    <!-- associo al main la funzione search e la richiamo -->
    <Header 
    @Search="Search"
    />
    <!-- passo al main fratello di header la stringa search che ho ricevuto dall'header in modo tale da filtrare dentro il main nella chiamata api
     -->
    <Main 
    :search="search"
    />
  </div>
</template>

<script>
import Header from '@/components/Header'
import Main from '@/components/Main'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      search:''
    }
  },
  methods:{
    /* funzione che uso per salvare in una variabile la stringa che mi serve */
    Search(search){
      this.search = search; 
      console.log(this.search);
      console.log(search);

    }
  }
}
</script>

<style lang="scss">
@import 'assets/scss/general.scss'

</style>
