<template>
  <div class="card-wrapper mb-5">
    <div class="item-card">
      <div class="front-card ">
        <img
        v-if="film.img === 'https://image.tmdb.org/t/p/w342null'"
        src="https://static.myo.it/presentation/img/NoImage.png"
        >
        <img
        v-else 
        class="card-poster" :src="film.img" :alt="film.title">
      </div>
      <div class="back-card d-flex flex-column p-3">
        <span class="my-2">Titolo: {{film.title}}</span>
        <span class="mb-2">Titolo originale: {{film.original_title}}</span>
        <span class="mb-2">Voto: <font-awesome-icon class="stars" v-for="(n, index) in film.vote" :key="`n-${index}`" icon="fa-solid fa-star" /></span>
        <span class="mb-2" v-if="film.language === 'en' || film.language === 'ja' || film.language === 'it'">
          Lingua originale: 
          <img v-if="film.language === 'en'" :src="flags.en" :alt="film.language">
          <img v-else-if="film.language === 'ja'" :src="flags.ja" :alt="film.language">
          <img v-else-if="film.language === 'it'" :src="flags.it" :alt="film.language">
        </span>
        <span class="mb-2" v-else>Lingua: {{film.language}}</span>
        <span
        v-if="film.overview === ''">
        Trama non disponibile
        </span> 
        <span v-else
        class="overview fs-5">Overview: <br> {{film.overview}}
        </span>
      </div>
    </div>
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

<style lang="scss">
.card-wrapper{
  position: relative;
  width: calc(100% / 4 - 50px);
  height: 410px;
  margin: 0 25px;
  &:hover .back-card{
    opacity: 1;
  }
  &:hover .front-card{
    opacity: 0;
  }
}

.item-card{
  width: 100%;
  height: 100%;
  .front-card{
    transition: all 0.5s ease-in-out; 
    img{
      height: 410px;
      width: 100%;
    }
  }
}

.back-card{
  opacity: 0;
  position: absolute;
  bottom: 0;
  right: 0;
  height: 100%;
  width: 100%;
  background-color: rgba($color: #221f1f, $alpha: 0.7);
  color: white;
  span img{
    width: 20px;
  }
  span.overview{
    overflow: scroll;
  }
  .stars{
    color: yellow;
  }
  transition: all 0.5s ease-in-out; 
}

</style>