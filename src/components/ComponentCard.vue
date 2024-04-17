<template>
    <ul>
        <li v-for=" (movie, i) in store.movies" :key="movie.id">
            <h1>{{ movie.title }}</h1>
            <p>{{ movie.originalTitle }}</p>
            <p>{{ movie.language }}</p>
            <p>{{ movie.vote }}</p>
        </li>

    </ul>
    <ul>
        <li v-for=" (serie, j) in store.series" :key="serie.id">
            <h1>{{ serie.titleSerie }}</h1>
            <p>{{ serie.originalTitleSerie }}</p>
            <p>{{ serie.languageSerie }}</p>
            <p>{{ serie.voteSerie }}</p>
        </li>

    </ul>
</template>

<script>
import { store } from '../store.js'

export default {
    data() {
        return {
            store: store,

        }
    },

}
</script>

<style lang="scss" scoped>
.en {
    background-image: url(../../public/img/en.png);
    background-size: cover;
    width: 10px;
}
</style>