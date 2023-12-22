<template>
    <!-- <img :src="`../assets/img/png100px/${film.original_language}.png`" alt="">
    <img src="../assets/img/png100px/it.png" alt=""> -->
    <main>
        <section class="film-section align-content-start">
            <h1>Film</h1>
            <FilmCard v-for="film in requestedFilms" :title="film.title" :poster_path="film.poster_path"
                :original_title="film.original_title" :original_language="film.original_language"
                :vote_average="film.vote_average" :overview="film.overview" />
        </section>
        <section class="series-section align-content-start">
            <h1>Serie TV</h1>
            <SeriesCard v-for="series in requestedTvSeries" :name="series.name" :poster_path="series.poster_path"
                :original_name="series.original_name" :original_language="series.original_language"
                :vote_average="series.vote_average" :overview="series.overview" />
        </section>
    </main>
</template>



<style lang="scss" scoped>
@use '../style/partials/variables' as *;
@use '../style/partials/mixins' as *;

main {
    height: 85vh;
    background-color: $bg-main;
    overflow: scroll;

    section {
        width: calc(100% - 9rem);
        margin: 0 4.5rem 1rem 4.5rem;
        @include flex(row, start, center);
        flex-wrap: wrap;

        h1 {
            width: 100%;
            font-size: 1.5rem;
            color: white;
            margin-bottom: 1.5rem;
        }

        /* &.film-section {

        }

        &.series-section {} */
    }
}
</style>

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