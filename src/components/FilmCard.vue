<template>
    <div v-for="film in requestedFilms">
        <img :src="`https://image.tmdb.org/t/p/w185/${film.poster_path}`" :alt="`${film.title} cover`">
        <p>titolo: {{ film.title }}</p>
        <p>titolo originale: {{ film.original_title }}</p>
        <p>lingua: {{ film.original_language.toUpperCase() }}</p>
        <!-- <img :src="`../assets/img/png100px/${film.original_language}.png`" alt="">
        <img src="../assets/img/png100px/it.png" alt=""> -->
        <img :src="`/src/assets/img/png100px/${film.original_language}.png`" alt="">
        <p>voto: {{ roundToFive(parseInt(film.vote_average)) }} /5</p>
    </div>
</template>

<script>
export default {
    props: {
        requestedFilms,
    },
    data() {
        return {

        }
    },
    methods: {

    }

}
</script>

<style lang="scss" scoped></style>