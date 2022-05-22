<template>
  <main>
    <div class="container d-flex">
      <FilmsComponent
      v-for="(film, index) in filmsToDisplay" :key="`film-${index}`"
      :film = film
      />
    </div>
  </main>
</template>

<script>
import FilmsComponent from './FilmsComponent.vue'
export default {
  components: { FilmsComponent },
  name: 'MainC',
  props: {
    filmsToDisplay: Array
  }
}
</script>

<style>

</style>