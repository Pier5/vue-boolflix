<template>
  <main>
    <div class="no-results" v-if="movies == null">Cerca tra migliaia di film e serie tv</div>
    <div class="no-results" v-else-if="movies == '' && series == ''">Nessun risultato. Prova a cercare ancora</div>
    <div v-else>
      <section class="movies-titles">
      <h1 v-if="movies == ''"></h1>
      <h1 v-else>Lista film:</h1>
      <div class="container">
        <BoolflixCards
          v-for="element in movies"
          :key="element.id"
          :card-data="element"
          :card-type="listType"
        />
      </div>
    </section>
    <section class="series-titles">
      <h1 v-if="series == ''"></h1>
      <h1 v-else>Lista serie tv:</h1>
      <div class="container">
        <BoolflixCards
          v-for="element in series"
          :key="element.id"
          :card-data="element"
          :card-type="listTop"
        />
      </div>
  </section>
    </div>
  </main>
</template>

<script>
import BoolflixCards from './BoolflixCards.vue'

export default {
  name: 'MainBoolflix',
  data () {
    return {
      listType: 'movie',
      listTop: 'tv'
    }
  },
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
h1,
.no-results {
  margin-left: 65px;
  padding-top: 100px;
  text-transform: uppercase;
  color: white;
}
.no-results {
  font-size: 1.5rem;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

</style>
