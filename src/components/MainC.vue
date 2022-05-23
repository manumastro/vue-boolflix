<template>
  <main class="pt-5">
    <div class="container">

      <div
      v-if="filmsToDisplay.length > 0" 
      class="films-container d-flex flex-wrap mb-5">
        <h1 class="w-100">Film</h1>
        <FilmsComponent
        v-for="(film, index) in filmsToDisplay" :key="`film-${index}`"
        :film = film
        />
      </div>

      <div
      v-if="tvShowsToDisplay.length > 0" 
      class="tvShows d-flex flex-wrap">
        <h1 class="w-100">Serie Tv</h1>
        <TvShowsComponent
        v-for="(tvShow, index) in tvShowsToDisplay" :key="`tvShow-${index}`"
        :tvShow = tvShow
        />
      </div>

    </div>
  </main>
</template>

<script>
import FilmsComponent from './FilmsComponent.vue';
import TvShowsComponent from './TvShowsComponent.vue';
export default {
  components: {
    FilmsComponent,
    TvShowsComponent
  },
  name: 'MainC',
  props: {
    filmsToDisplay: Array,
    tvShowsToDisplay: Array
  }
}
</script>

<style lang="scss" scoped>
main{
  background-color: #f5f5f1;
}
.container{
  border: 1px solid green;
}
</style>