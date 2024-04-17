<template>
  <div>

    <input v-model="store.query" type="text" placeholder="Inserisci titolo">
    <button @click="functionBottom()">Invio</button>
    <ComponentCard />
  </div>
</template>

<script>
import ComponentCard from './ComponentCard.vue';
import { store } from '../store.js'
import axios from 'axios'
export default {
  components: {
    ComponentCard
  },
  data() {
    return {
      store: store,
      // title: [],
      // originalTitle: [],
      // language: [],
      // vote: [],

    }
  },
  methods: {
    funcionMovies() {
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: this.store.API_KEY,
            query: this.store.query

          }

        }).then((res) => {
          const data = res.data
          const result = data.results

          for (let i = 0; i < result.length; i++) {
            const img = result[i].poster_path
            const title = result[i].title
            const originalTitle = result[i].original_title
            const language = result[i].original_language
            const vote = result[i].vote_average
            this.store.movies.push({
              title,
              originalTitle,
              language,
              vote,
              img
            })

            // this.title.push(res.data.results[i].title),
            //   this.originalTitle.push(res.data.results[i].original_title),
            //   this.language.push(res.data.results[i].original_language),
            //   this.vote.push(res.data.results[i].vote_average),




            //   console.log(this.title, this.originalTitle, this.language, this.vote);
          }


        })

    },
    funcionSeries() {
      axios
        .get('https://api.themoviedb.org/3/search/tv', {
          params: {
            api_key: this.store.API_KEY,
            query: this.store.query

          }

        }).then((res) => {
          const dataSerie = res.data
          const resultSerie = dataSerie.results
          for (let j = 0; j < resultSerie.length; j++) {
            const img = result[j].poster_path
            const titleSerie = resultSerie[j].name
            const originalTitleSerie = resultSerie[j].original_name
            const languageSerie = resultSerie[j].original_language
            const voteSerie = resultSerie[j].vote_average
            this.store.series.push({
              titleSerie,
              originalTitleSerie,
              languageSerie,
              voteSerie,
              img
            })


          }


        })

    },
    functionBottom() {
      this.funcionMovies()
      this.funcionSeries()
    }
  }
}
</script>

<style lang="scss" scoped>
.bandiera-inglese {
  background-image: url(bandiera-inglese);
}
</style>