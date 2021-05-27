<template>
  <div class="p-3">
    
    <ul class="list-group">
      <li class="list-group-item">{{ card.title}}</li>
      <li class="list-group-item">{{ card.original_title  || card.original_name}}</li>
      <li class="list-group-item">{{ card.original_language }}</li>
      <li class="list-group-item"><flag :iso="bandiere()"/></li>
      <!-- <li class="list-group-item"><flag :iso="card.original_language === 'en' ? 'gb'+'it' : card.original_language"/></li> -->

      <!-- Math.ceil(card.vote_average/2) divide il numero di vote_average per due e in più arrotondo -->
      <li class="list-group-item">{{ Math.ceil(card.vote_average/2) }}</li>
      <li class="list-group-item">
        <div
        style="display:inline-block; "
        v-for="index in 5" :key="index"
        >
          <i 
          style="margin:2px"
          v-if="index < Math.ceil(card.vote_average/2)"
          class="fas fa-angry"></i>
          <i 
          v-else
          style="margin:2px"
          class="far fa-angry"></i>
        </div>
      </li>
    </ul>
    <img :src="'https://image.tmdb.org/t/p/w342' + card.poster_path" alt="">
  </div>
</template>

<script>
export default {
  name:'Card',
  props:{
    card: Object
  },
  methods:{
    bandiere(){
      if(this.card.original_language === 'en'){
        return 'gb';
      }else if(this.card.original_language === 'ja'){
        return 'jp';
      }
      else{
        return this.card.original_language;
      }
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/general.scss';

</style>