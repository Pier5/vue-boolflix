<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img class="cover-img" :src="'https://image.tmdb.org/t/p/w300'+CardData.poster_path" :alt="CardData.original_title ? CardData.original_title : CardData.original_name">
      </div>
      <div class="flip-card-back">
        <h1>{{ CardData.original_title ? CardData.original_title : CardData.original_name }}</h1>
        <h2>{{ CardData.title ? CardData.title : CardData.name }}</h2>
        <lang-flag v-if="checkLangFlag(CardData.original_language)" :iso="CardData.original_language" class="lang" />
        <div v-else class="lang">{{ CardData.original_language }}</div>
        <div class="rating">{{ CardData.vote_average }}</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'MoviesCards',
  props: {
    CardData: Object
  },
  data () {
    return {
      arrLang: [
        'en',
        'fr',
        'de',
        'it',
        'ja',
        'pt',
        'ru',
        'es'
      ]
    }
  },
  methods: {
    checkLangFlag (flag) {
      if (this.arrLang.includes(flag)) {
        return this.arrLang
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.cover-img {
  width: 100%;
  height: 100%;
  background-size: contain;
}
.flip-card {
  width: 300px;
  height: 400px;
  margin: 20px;
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 1s;
  transform-style: preserve-3d;
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}
.flip-card-front {
  background-color: #bbb;
  color: black;
}
.flip-card-back {
  width: 100%;
  height: 100%;
  background-color: #181818;
  color: white;
  transform: rotateY(180deg);
  h1,
  h2 {
    text-align: center;
    padding: 2rem;
  }
  .lang {
    padding-bottom: 1.2rem;
    font-size: 1.5rem;
  }
}
</style>
