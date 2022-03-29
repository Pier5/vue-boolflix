<template>
  <div class="cards">
    <h1>{{ cardData.original_title }}</h1>
  </div>
</template>

<script>
export default {
  name: 'MoviesCards',
  props: {
    cardData: Object
  }
}
</script>

<style>

</style>
