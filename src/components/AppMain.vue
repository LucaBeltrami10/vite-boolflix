<template>
    <div v-for="film in axiosResponse.data.results">
        <p>titolo: {{ film.title }}</p>
        <p>titolo originale: {{ film.original_title }}</p>
        <p>lingua: {{ film.original_language }}</p>
        <p>voto: {{ film.vote_average }}/10</p>
    </div>
</template>

<script>
export default {
    props: {
        lookedFor: String,
        axiosResponse: Object,
    }

}
</script>

<style lang="scss" scoped>
div {
    background-color: rgb(240, 98, 98);
    margin: 3rem;
}
</style>