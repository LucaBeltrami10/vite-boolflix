<template>
    <!-- <img :src="`../assets/img/png100px/${film.original_language}.png`" alt="">
    <img src="../assets/img/png100px/it.png" alt=""> -->
    <main>
        <section class="film-section">
            <FilmCard v-for="film in requestedFilms" :title="film.title" :poster_path="film.poster_path"
                :original_title="film.original_title" :original_language="film.original_language"
                :vote_average="film.vote_average" />
        </section>
        <section class="series-section">
            <SeriesCard v-for="series in requestedTvSeries" :name="series.name" :poster_path="series.poster_path"
                :original_name="series.original_name" :original_language="series.original_language"
                :vote_average="series.vote_average" />
        </section>
    </main>
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
@use '../style/partials/variables' as *;
@use '../style/partials/mixins' as *;

main {
    height: 85vh;
    background-color: $bg-main;
    overflow: scroll;

    section.film-section {
        @include flex(row, space-between, center);
        flex-wrap: wrap;

    }

    section.series-section {
        @include flex(row, space-between, center);
        flex-wrap: wrap;

    }





}
</style>