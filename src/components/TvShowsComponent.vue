<template>
  <div class="card-wrapper mb-5">
    <div class="item-card">
      <div class="front-card ">
        <img
        v-if="tvShow.img === 'https://image.tmdb.org/t/p/w342null'"
        src="https://static.myo.it/presentation/img/NoImage.png"
        >
        <img
        v-else 
        class="card-poster" :src="tvShow.img" :alt="tvShow.title">
      </div>
      <div class="back-card d-flex flex-column p-3">
        <span class="my-2">Titolo: {{tvShow.title}}</span>
        <span class="mb-2">Titolo originale: {{tvShow.original_title}}</span>
        <span class="mb-2">Voto: <font-awesome-icon class="stars" v-for="(n, index) in tvShow.vote" :key="`n-${index}`" icon="fa-solid fa-star" /></span>
        <span class="mb-2" v-if="tvShow.language === 'en' || tvShow.language === 'ja' || tvShow.language === 'it'">
          Lingua originale: 
          <img v-if="tvShow.language === 'en'" :src="flags.en" :alt="tvShow.language">
          <img v-else-if="tvShow.language === 'ja'" :src="flags.ja" :alt="tvShow.language">
          <img v-else-if="tvShow.language === 'it'" :src="flags.it" :alt="tvShow.language">
        </span>
        <span class="mb-2" v-else>Lingua: {{tvShow.language}}</span>
        <span
        v-if="tvShow.overview === ''">
        Trama non disponibile
        </span> 
        <span v-else
        class="overview fs-5">Overview: <br> {{tvShow.overview}}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'tvShowsComponent',
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

<style lang="scss">

</style>