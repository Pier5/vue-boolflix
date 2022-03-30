<template>
  <div class="cards">
    <h1>{{ CardData.original_title ? CardData.original_title : CardData.original_name }}</h1>
    <h2>{{ CardData.title ? CardData.title : CardData.name }}</h2>
    <div class="lang">{{ CardData.original_language }}</div>
    <div class="rating">{{ CardData.vote_average }}</div>
  </div>
</template>

<script>
export default {
  name: 'MoviesCards',
  props: {
    CardData: Object
  }
}
</script>

<style lang="scss" scoped>
.cards {
  width: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border: 1px solid black;
  margin: 10px;
  padding: 5rem 2rem;
  h1,
  h2 {
    text-align: center;
    padding: 2rem 0;
  }
  .lang {
    padding-bottom: 1.2rem;
  }
}
</style>
