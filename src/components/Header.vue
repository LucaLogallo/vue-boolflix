<template>
  <div class="wrapper ">

    <div class="container d-flex justify-content-center align-items-center">

      <div class="m-2">
        <input 
        class="form-control p-2 rounded-pill"
        v-model="textSearch"
        type="text">
      </div>

      <div class="m-2">

        <!-- al click passerò alla funzione startSearch un oggetto che conterrò due informazioni
        text= al v-model dell'input 
        type= tipo di cosa da ricercare tra (movie,tv ed entrambe)ù
        quindi ripeterò l'emit per ogni click di ogni bottone cambiando in base al bottone il type
        -->

        <button 
        @click="$emit('startSearch', {text:textSearch,type:'movie'})"
        class="p-2 rounded-pill">CERCA FILM</button>
      </div>

      <div class="m-2">
        <button 
        @click="$emit('startSearch', {text:textSearch,type:'tv'})"
        class="p-2 rounded-pill">CERCA SERIE TV</button>
      </div>

      <div class="m-2">
        <button 
        @click="$emit('startSearch', {text:textSearch,type:'all'})"
        class="p-2 rounded-pill">CERCA TUTTO</button>
      </div>

    </div>

  </div>
</template>

<script>

export default {
  name: 'Header',
  data(){
    return{
      textSearch:''
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';
.wrapper{
  height: 70px;
  background-color: darkslategray;
  input{
    border-color: red;
  }
  div{
    button{
      border-color: red;
      color: red;
    }
  }
}
</style>