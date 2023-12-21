<template>
    <div v-for="film in requestedFilms">
        <p>titolo: {{ film.title }}</p>
        <p>titolo originale: {{ film.original_title }}</p>
        <p>lingua: {{ film.original_language }}</p>
        <p>voto: {{ film.vote_average }}/10</p>
    </div>
</template>

<script>
export default {
    props: {
        requestedFilms: Object,
    }

}
</script>

<style lang="scss" scoped>
div {
    background-color: rgb(240, 98, 98);
    margin: 3rem;
}
</style>