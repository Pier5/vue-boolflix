<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-if="CardData.poster_path != null" class="cover-img" :src="'https://image.tmdb.org/t/p/w342' + CardData.poster_path" :alt="CardData.original_title ? CardData.original_title : CardData.original_name">
        <img v-else :src="'https://picsum.photos/310/490'" :alt="CardData.original_title ? CardData.original_title : CardData.original_name">
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
          <lang-flag v-if="checkLangFlag(CardData.original_language)" :iso="CardData.original_language" :squared="false" class="lang" />
          <div v-else class="lang">{{ CardData.original_language }}</div>
        </div>
        <div class="ratings">
          <h2 class="text-description">Voto:</h2>
          <i class="fa-solid fa-star" v-for="star in starsRating(CardData.vote_average)" :key="star.id"></i>
          <i class="fa-regular fa-star" v-for="starless in starsRatingDifferece(CardData.vote_average)" :key="starless.id"></i>
        </div>
        <div class="ratings">
          <h1>{{ CardData.overview }}</h1>
        </div>
        <div class="cast">
          <h2 class="text-description">Cast:</h2>
          <div v-for="actor in arrMoviesActors" :key="actor.credit_id">{{ actor.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'BoolflixCards',
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
      ],
      arrMoviesActors: null,
      arrSeriesActors: null,
      maxVote: 10
    }
  },
  created () {
    axios.get(`https://api.themoviedb.org/3/movie/${this.CardData.id}/credits?api_key=553882726aa4b4cb9f8231098d4aef32`)
      .then((response) => {
        this.arrMoviesActors = response.data.cast
        this.arrMoviesActors.splice(5)
      })
      .catch(() => {
        const error = document.createElement('div')
        const container = document.querySelector('.cast')
        error.innerHTML = 'File non trovato'
        container.append(error)
      })
  },
  methods: {
    checkLangFlag (flag) {
      if (this.arrLang.includes(flag)) {
        return this.arrLang
      }
    },
    starsRating (vote) {
      return Math.ceil(vote / 2)
    },
    starsRatingDifferece (vote) {
      return Math.floor((this.maxVote - vote) / 2)
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
  border: 5px solid  #34568B;
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
  overflow-y: auto;
  .original-name,
  .title-name,
  .language-flag,
  .ratings,
  .cast {
    margin: 1.1rem;
  }
  h1,
  h2 {
    color: #D65076;
    font-size: .8rem;
  }
  .text-description {
    color: #45B8AC;
    padding-top: .5rem;
  }
  .lang {
    padding-bottom: 1.2rem;
    font-size: 1.5rem;
  }
  .fa-solid {
  color: gold;
}
}
</style>
