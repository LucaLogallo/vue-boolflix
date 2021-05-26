<template>
  <div class="wrap">
    <div class="headerRight">
      <img src="" alt="">
    </div>

    <div class="headerRight">
    <input type="text"
    class="form-control"
    placeholder="cerca"
    v-model="search" 
    @keyup.enter="MovieDaCercare"
    >
    <!-- al keyuip.enter richiamo la funzione MovieDaCercare -->
    <button
    @click="MovieDaCercare"
    class="btn btn-primary">Cerca</button>
    <!-- al click del bottone richiamo la funzione MovieDaCercare -->
    </div>
  </div>
</template>

<script>

export default {
  name:'Header',
  data(){
    return{
      search:""
    }
  },
  methods:{
    /* funzione che richiamo per passare il parametro vmoldel search al padre richiamando la funzione del padre con nome Search per poi poter passare il parametro vmolde search al fratello  */
    MovieDaCercare(){
      this.$emit('Search', this.search);
      /* emit per poter richiamare la funzione di prima */
      this.search=""
    }
  }

}
</script>

<style lang="scss" scoped>
  .wrap{
    height: 100px;
    background-color: red;
    display: flex;
    justify-content: space-between;
    align-content: center;
    padding: 2%;
    .headerRight{
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      input{
        height: 25px;
        margin: 10px;
      }
      button{
        padding: 5px;
      }
    }
  }
</style>