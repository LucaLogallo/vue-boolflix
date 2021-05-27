<template>
  <div class="container">
    <h1>{{titolo[type]}}</h1>
  </div>
</template>

<script>
export default {
  name:'Card',
  props:{
    type: String,
    titolo: Object
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>