<template>
  <div id="app">
    <HeaderC @search="searchFunction" />
    <MainC
    :filmsToDisplay = apiMovies 
    :tvShowsToDisplay = apiTvShows /> 
  </div>
</template>

<script>
import axios from 'axios'
import HeaderC from './components/HeaderC.vue';
import MainC from './components/MainC.vue';

export default {
  name: 'App',
  components: {
    HeaderC,
    MainC
  },
  data(){
    return{
      apiUrlMovie: 'https://api.themoviedb.org/3/search/movie',
      apiUrlTv: 'https://api.themoviedb.org/3/search/tv',
      apiParams: {
        api_key: 'aaeab3237d6878f2cb8d8227529ccffd',
        language: 'it-IT',
        query: ''
      },
      apiResult: [],
      apiMovies: [],
      apiTvShows: [],
    }
  },
  methods:{
    searchFunction(searchInput){
      this.apiParams.query = searchInput;
      this.getApiMovies();
      this.getApiTv();
    },
    getApiMovies(){
      axios.get(this.apiUrlMovie, {
        params: this.apiParams
      })
      .then( result => {
        this.apiResult = result.data.results
        this.decomposeMoviesArray();
      })
      .catch( error=> {
        console.log(error);
      })
    },
    getApiTv(){
      axios.get(this.apiUrlTv, {
        params: this.apiParams
      })
      .then( result => {
        this.apiResult = result.data.results
        this.decomposeTvArray();
      })
      .catch( error=> {
        console.log(error);
      })
    },
    decomposeMoviesArray(){
      this.apiMovies = this.apiResult.map(el => ({
        title: el.title,
        original_title: el.original_title,
        language: el.original_language,
        vote: el.vote_average
      }))
    },
    decomposeTvArray(){
      this.apiTvShows = this.apiResult.map(el => ({
        title: el.name,
        original_title: el.original_name,
        language: el.original_language,
        vote: el.vote_average
      }))
    } 
  },
}
</script>

<style lang="scss">
@import '../src/assets/style/_general.scss';
</style>
