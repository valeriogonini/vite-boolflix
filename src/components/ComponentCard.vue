<template>
    <ul>
        <li v-for=" (movie, i) in store.movies" :key="movie.id">
            <h1>{{ movie.title }}</h1>
            <p>{{ movie.originalTitle }}</p>
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.img}`" alt="">
            <img class="w-nation" :src="`/img/${movie.language}.png`">
            <p>{{ movie.vote }}</p>
        </li>

    </ul>
    <ul>
        <li v-for=" (serie, j) in store.series" :key="serie.id">
            <h1>{{ serie.titleSerie }}</h1>
            <p>{{ serie.originalTitleSerie }}</p>
            <img :src="`https://image.tmdb.org/t/p/w342/${serie.img}`" alt="">
            <img class="w-nation" :src="`/img/${serie.languageSerie}.png`">
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
.w-nation {
    width: 20px;
}
</style>