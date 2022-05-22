<template>
  <header class="d-flex align-items-center justify-content-center">
      <div id="logo" class="h-100">
        <a class="d-flex align-items-center h-100 " href="#">
          <img class="h-50" src="https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png" alt="netflix-logo">
        </a>
      </div>
      <div id="input-field" class="d-flex">
        <input
        v-model.trim="searchInput"
        @keyup.enter="searchFunction"
        type="text" class="form-control fs-5 me-5" placeholder="Inserire film o serie tv">
        <button
        @click="searchFunction" 
        class="btn btn-danger">Cerca</button>
      </div>
  
  </header>
</template>

<script>
export default {
  name: 'HeaderC',
  data(){
    return{
      searchInput: ''
    }
  },
  methods:{
    searchFunction(){
      this.$emit('search', this.searchInput);
    }
  }
}
</script>

<style lang="scss" scoped>
  header{
    height: 100px;
    background-image: linear-gradient(#060606, #292929);
    #logo{
      margin-right: 20vw;
    }
    #input-field{
      width: 20vw;
    }
  }
</style>