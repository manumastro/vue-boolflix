<template>
  <div class="d-flex flex-column tvShow-card mb-5">
    <img :src="tvShow.img" :alt="tvShow.title">

    <span>{{tvShow.title}}</span>
    <span>{{tvShow.original_title}}</span>
    <span v-if="tvShow.language === 'en' || tvShow.language === 'ja' || tvShow.language === 'it'">
      <img v-if="tvShow.language === 'en'" :src="flags.en" :alt="tvShow.language">
      <img v-else-if="tvShow.language === 'ja'" :src="flags.ja" :alt="tvShow.language">
      <img v-else-if="tvShow.language === 'it'" :src="flags.it" :alt="tvShow.language">
    </span>
    <span v-else>{{tvShow.language}}</span>
    <span class="stars"><font-awesome-icon v-for="(n, index) in tvShow.vote" :key="`n-${index}`" icon="fa-solid fa-star" /></span>
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
    tvShow: Object
  }
}
</script>

<style lang="scss" scoped>
.tvShow-card{
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