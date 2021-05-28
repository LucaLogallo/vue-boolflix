<template>
  <div class="wrap">

    <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img :src="card.poster_path === null ? '@/assets/img/default.jpg' :'https://image.tmdb.org/t/p/w342' + card.poster_path" alt="">
      </div>
      <div class="flip-card-back">
        <h1>{{ card.title }}</h1> 
        <p>Titolo: {{ card.original_title  || card.original_name}}</p> 
        <p>Lingua: {{ card.original_language }}</p>
        <p><flag :iso="bandiere()"/></p>
        <p>Voto: {{ Math.round(card.vote_average/2) }}</p>
        <div>
          <span style="font-weigth:bold">Voto: </span>
          <div
            style="display:inline-block; "
            v-for="index in 5" :key="index"
          >
          
          <i 
            style="margin:2px"
            v-if="index <= Math.round(card.vote_average/2)"
            class="fas fa-angry">
          </i>
          <i 
            v-else
            style="margin:2px"
            class="far fa-angry">
          </i>
          </div>
        </div>
        <p class="overview">{{card.overview}}</p>
      </div>
    </div>
    </div>

    <!-- <ul class="list-group">
      <li class="list-group-item">{{ card.title}}</li>
      <li class="list-group-item">{{ card.original_title  || card.original_name}}</li>
      <li class="list-group-item">{{ card.original_language }}</li>
      <li class="list-group-item"><flag :iso="bandiere()"/></li>
      <li class="list-group-item"><flag :iso="card.original_language === 'en' ? 'gb'+'it' : card.original_language"/></li> 

       Math.ceil(card.vote_average/2) divide il numero di vote_average per due e in più arrotondo 
      <li class="list-group-item">{{ Math.round(card.vote_average/2) }}</li>
      <li class="list-group-item">
        <div
        style="display:inline-block; "
        v-for="index in 5" :key="index"
        >
          <i 
          style="margin:2px"
          v-if="index <= Math.round(card.vote_average/2)"
          class="fas fa-angry"></i>
          <i 
          v-else
          style="margin:2px"
          class="far fa-angry"></i>
        </div>
      </li>
    </ul>
    <img :src="'https://image.tmdb.org/t/p/w342' + card.poster_path" alt="">
   -->
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

<style lang="scss" scoped>
@import '@/assets/scss/general.scss';

.wrap{
  padding: 1px;
}

.flip-card {
  background-color: transparent;
  width: 250px;
  height: 400px;
  perspective: 1000px;
  
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(171,6,15,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  width: 250px;
  height: 400px;
}

.flip-card-front {
  color: black;
  img{
    height: 100%;
    width: 100%;
  }
}

.flip-card-back {
  background-color: rgba(171,6,15,0.8);
  color: white;
  transform: rotateY(180deg);
  overflow: scroll;
}

</style>