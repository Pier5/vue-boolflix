<template>
  <header>
    <h1 class="logo-text">Boolflix</h1>
    <form @submit.prevent="$emit('search', searchText)">
      <label for="search">
        <input class="search-bar" type="text" placeholder="Cerca il tuo film preferito" v-model="searchText">
        <button class="btn-search">Cerca</button>
      </label>
    </form>
  </header>
</template>

<script>

export default {
  name: 'HeaderBoolflix',
  data () {
    return {
      searchText: ''
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
  .search-bar {
    height: 2rem;
    padding: .4rem;
  }
  .btn-search {
    height: 2rem;
    color: white;
    background-color: red;
    padding: .3rem;
  }
}
</style>
