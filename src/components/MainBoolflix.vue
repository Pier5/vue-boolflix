<template>
  <main>
    <div class="container">
      <MoviesCards
      v-for="element in movies"
      :key="element.id"
      :card-data="element"
      />
    </div>
  </main>
</template>

<script>
import MoviesCards from './MoviesCards.vue'

export default {
  name: 'MainBoolflix',
  props: {
    movies: Array,
    series: Array
  },
  components: {
    MoviesCards
  }
}
</script>

<style>

</style>
