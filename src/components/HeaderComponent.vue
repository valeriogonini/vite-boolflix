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
      store: store

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
          console.log(res.data.results);
        })
    }
  }
}
</script>

<style lang="scss" scoped></style>