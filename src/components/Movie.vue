<template>
  <div>
    <ul>
      <li>{{movie.original_title}}</li>
      
    </ul>
  </div>
</template>

<script>

export default {
  name:'Movie',
  props:{
    movie:Object
  }
}
</script>

<style>

</style>