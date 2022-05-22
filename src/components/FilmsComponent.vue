<template>
  <div class="d-flex flex-column film-card">
    <span>{{film.title}}</span>
    <span>{{film.original_title}}</span>
    <span>{{film.title}}</span>
    <span>{{film.vote}}</span>
  </div>
</template>

<script>
export default {
  name: 'FilmsComponent',
  props:{
    film: Object
  }
}
</script>

<style lang="scss" scoped>
.film-card{
  flex-basis: 25%;
  border: 1px solid red;
  span{
    border: 1px solid blue;
  }
}
</style>