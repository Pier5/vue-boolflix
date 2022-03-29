<template>
  <header>
    <h1 class="logo-text">Boolflix</h1>
    <SearchBar @search="getSearch"/>
  </header>
</template>

<script>
import SearchBar from './SearchBar.vue'

export default {
  name: 'HeaderBoolflix',
  components: {
    SearchBar
  },
  methods: {
    getSearch (element) {
      this.$emit('research', element)
    }
  }
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  background-color: black;
  height: 5rem;
  padding: 0 1rem;
  .logo-text {
    color: red;
    margin-right: auto;
    text-transform: uppercase;
  }
}
</style>
