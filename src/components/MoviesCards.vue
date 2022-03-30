<template>
  <div class="cards">
    <h1>{{ CardData.original_title }}</h1>
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

<style>

</style>
