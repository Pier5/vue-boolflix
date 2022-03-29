<template>
  <div class="search-titles">
    <input class="search-bar" type="text" placeholder="Cerca il tuo film preferito" v-model="searchText">
    <button class="btn-search" @click="$emit('search', searchText) ">Cerca</button>
  </div>
</template>

<script>

export default {
  name: 'SearchBar',
  data () {
    return {
      searchText: ''
    }
  }
}
</script>

<style lang="scss" scoped>
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
</style>
