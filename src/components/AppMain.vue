<template>
    <div v-for="film in requestedFilms">
        <img :src="`https://image.tmdb.org/t/p/w185/${film.poster_path}`" :alt="`${film.title} cover`">
        <p>titolo: {{ film.title }}</p>
        <p>titolo originale: {{ film.original_title }}</p>
        <p>lingua: {{ film.original_language }}</p>
        <p>voto: {{ film.vote_average }}/10 oppure {{ roundToFive(parseInt(film.vote_average)) }} /5</p>
    </div>
    <div v-for="series in requestedTvSeries">serie rilevata</div>
</template>

<script>
export default {
    props: {
        requestedFilms: Object,
        requestedTvSeries: Object,
    },
    data() {
        return {

        }
    },
    methods: {
        roundToFive(number) {
            return Math.floor(number / 2)
        },

    }

}
</script>

<style lang="scss" scoped>
div {
    background-color: rgb(240, 98, 98);
    margin: 3rem;
}
</style>