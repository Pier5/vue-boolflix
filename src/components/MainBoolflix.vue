<template>
  <main>
    <section v-show="movies.length" class="movies-titles">
      <h1>Lista film:</h1>
      <div class="container">
        <BoolflixCards
          v-for="element in movies"
          :key="element.id"
          :card-data="element"
        />
      </div>
    </section>
    <section v-show="series.length" class="series-titles">
      <h1>Lista serie tv:</h1>
      <div class="container">
        <BoolflixCards
          v-for="element in series"
          :key="element.id"
          :card-data="element"
        />
      </div>
    </section>
  </main>
</template>

<script>
import BoolflixCards from './BoolflixCards.vue'

export default {
  name: 'MainBoolflix',
  props: {
    movies: Array,
    series: Array
  },
  components: {
    BoolflixCards
  }
}
</script>

<style lang="scss" scoped>
h1 {
  margin-top: 40px;
  margin-left: 65px;
  text-transform: uppercase;
  color: white;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

</style>
