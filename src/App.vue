<template>
<div id="app">
    <HeaderBoolflix @research="strSearchMovies"/>
    <MainBoolflix :stringa-ricerca="strSearch"/>
  </div>
</template>

<script>
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolflix from './components/MainBoolflix.vue'

export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolflix
  },
  data () {
    return {
      strSearch: ''
    }
  },
  methods: {
    strSearchMovies (element) {
      this.strSearch = element
    }
  }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
</style>
