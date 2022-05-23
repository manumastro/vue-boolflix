<template>
  <div class="d-flex flex-column film-card mb-5">
    <img :src="film.img" :alt="film.title">
    <span>{{film.title}}</span>
    <span>{{film.original_title}}</span>
    <span v-if="film.language === 'en' || film.language === 'ja' || film.language === 'it'">
      <img v-if="film.language === 'en'" :src="flags.en" :alt="film.language">
      <img v-else-if="film.language === 'ja'" :src="flags.ja" :alt="film.language">
      <img v-else-if="film.language === 'it'" :src="flags.it" :alt="film.language">
    </span>
    <span v-else>{{film.language}}</span>
    <span class="stars"><font-awesome-icon v-for="(n, index) in film.vote" :key="`n-${index}`" icon="fa-solid fa-star" /></span>
  </div>
</template>

<script>
export default {
  name: 'FilmsComponent',
  data(){
    return{
      flags : 
      {
        en: 'https://wiki2.railml.org/images/b/b8/UK_flag.png',
        ja: 'https://cdn.countryflags.com/thumbs/japan/flag-round-250.png',
        it: 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1500px-Flag_of_Italy.svg.png'
      }
    }
  },
  props:{
    film: Object
  }
}
</script>

<style lang="scss" scoped>
.film-card{
  width: calc(100% / 4 - 50px);
  margin: 0 25px;
  
  border: 1px solid red;
  span{
    border: 1px solid blue;
    img{
      width: 30px;
    }
    &.stars{
      color: rgb(209, 209, 54);
    }
  }
}
</style>