<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img class="cover-img" :src="'https://image.tmdb.org/t/p/w300' + CardData.poster_path" :alt="CardData.original_title ? CardData.original_title : CardData.original_name">
      </div>
      <div class="flip-card-back">
        <div class="original-name">
          <h1 class="text-description">Titolo originale:</h1>
          <h1>{{ CardData.original_title ? CardData.original_title : CardData.original_name }}</h1>
        </div>
        <div class="title-name">
          <h2 class="text-description">Titolo:</h2>
          <h2>{{ CardData.title ? CardData.title : CardData.name }}</h2>
        </div>
        <div class="language-flag">
          <h2 class="text-description">Lingua:</h2>
          <lang-flag v-if="checkLangFlag(CardData.original_language)" :iso="CardData.original_language" class="lang" />
          <div v-else class="lang">{{ CardData.original_language }}</div>
        </div>
        <div class="ratings">
          <h2 class="text-description">Voto:</h2>
          <div v-if="CardData.vote_average == 0">Ancora nessun voto assegnato</div>
          <span v-else v-for="stars in starsRating(CardData.vote_average)" :key="stars" >&#9733;</span>
        </div>
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
    },
    starsRating (vote) {
      return Math.ceil(vote / 2)
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
  width: 320px;
  height: 500px;
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
  .original-name,
  .title-name,
  .language-flag,
  .ratings {
    margin: 1.4rem;
  }
  h1,
  h2 {
    color: #D65076;
  }
  .text-description {
    color: #45B8AC;
    padding-top: .5rem;
  }
  .lang {
    padding-bottom: 1.2rem;
    font-size: 1.5rem;
  }
}
</style>
