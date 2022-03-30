<template>
<div id="app">
    <HeaderBoolflix @search="reachData"/>
    <MainBoolflix :movies="arrMovies" :series="arrSeries" />
  </div>
</template>

<script>
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolflix from './components/MainBoolflix.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolflix
  },
  data () {
    return {
      api_key: '553882726aa4b4cb9f8231098d4aef32',
      arrMovies: [],
      arrSeries: []
    }
  },
  methods: {
    reachData (searchText) {
      if (searchText !== '') {
        const obj = {
          api_key: this.api_key,
          language: 'it-IT',
          query: searchText
        }
        this.axiosCall('movie', obj)
        this.axiosCall('tv', obj)
      }
    },
    axiosCall (searchType, obj) {
      axios('https://api.themoviedb.org/3/search/' + searchType, {
        params: obj
      })
        .then((response) => {
          if (searchType === 'movie') {
            this.arrMovies = response.data.results
          } else {
            this.arrSeries = response.data.results
          }
        })
    }
  }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
</style>
