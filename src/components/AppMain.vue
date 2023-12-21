<template>
    <!-- <img :src="`../assets/img/png100px/${film.original_language}.png`" alt="">
    <img src="../assets/img/png100px/it.png" alt=""> -->

    <FilmCard v-for="film in requestedFilms" :title="film.title" :poster_path="film.poster_path"
        :original_title="film.original_title" :original_language="film.original_language"
        :vote_average="film.vote_average" />

    <SeriesCard v-for="series in requestedTvSeries" :name="series.name" :poster_path="series.poster_path"
        :original_name="series.original_name" :original_language="series.original_language"
        :vote_average="series.vote_average" />
</template>

<script>
import FilmCard from './FilmCard.vue';
import SeriesCard from './SeriesCard.vue';

export default {
    components: {
        FilmCard,
        SeriesCard,
    },
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