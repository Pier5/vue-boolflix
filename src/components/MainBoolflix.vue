<template>
  <main>
    <div class="container">
      <MoviesCards
        v-for="card in searchMovies"
        :key="card.original_title"
        :card-data="card"
      />
    </div>
  </main>
</template>

<script>
import MoviesCards from './MoviesCards.vue'
import axios from 'axios'

export default {
  name: 'MainBoolflix',
  data () {
    return {
      arrMovies: null
    }
  },
  components: {
    MoviesCards
  },
  props: {
    stringaRicerca: String
  },
  created () {
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=553882726aa4b4cb9f8231098d4aef32&query=stringaRicerca')
      .then((response) => {
        this.arrMovies = response.data.results
      })
  },
  methods: {
    searchMovies () {
      return this.arrMovies.filter((card) => {
        return card.original_title.toLowerCase().includes(this.stringaRicerca.toLowerCase())
      })
    }
  }
}
</script>

<style>

</style>
