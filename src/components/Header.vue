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
    >
    <button
    @click="$emit('Search', search)"
    
    class="btn btn-primary">Cerca</button>
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