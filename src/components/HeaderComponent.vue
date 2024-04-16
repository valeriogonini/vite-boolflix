<template>
  <div>
    <input type="text" placeholder="Inserisci titolo">
    <button @click="funcionButton()">Invio</button>
  </div>
</template>

<script>
import { store } from '../store.js'
import axios from 'axios'
export default {
  data() {
    return {
      store: store,
      title: [],
      originalTitle: [],
      language: [],
      vote: [],

    }
  },
  methods: {
    funcionButton() {
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: this.store.API_KEY,
            query: this.store.query

          }

        }).then((res) => {
          for (let i = 0; i < 10; i++)

            this.title.push(res.data.results[i].title),
              this.originalTitle.push(res.data.results[i].original_title),
              this.language.push(res.data.results[i].original_language),
              this.vote.push(res.data.results[i].vote_average),




              console.log(this.title, this.originalTitle, this.language, this.vote);
        })
    }
  }
}
</script>

<style lang="scss" scoped></style>