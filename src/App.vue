<template>
  <div id="app">
    <HeaderC @search="searchFunction" />
    <MainC :filmsToDisplay = apiObjectProp />
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
      inputToSearch: '',
      apiResult: [],
      apiObjectProp: []
    }
  },
  methods:{
    searchFunction(searchInput){
      this.inputToSearch = searchInput;
      this.getApi();
    },
    getApi(){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=aaeab3237d6878f2cb8d8227529ccffd&language=it-IT&query=${this.inputToSearch}`)
      .then( result => {
        this.apiResult = result.data.results
        this.decompose();
      })
      .catch( error=> {
        console.log(error);
      })
    },
    decompose(){
      // this.apiResult.forEach((el, index) => {
        
      //   this.apiObjectProp = {title : el[index].title} 
      // })
      this.apiObjectProp = this.apiResult.map(el => ({
        title: el.title,
        original_title: el.original_title,
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
