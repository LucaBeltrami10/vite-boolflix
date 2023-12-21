<template>
    <article class="my-3">
        <img :src="`https://image.tmdb.org/t/p/w185/${poster_path}`" :alt="`${title} cover`">
        <div class="d-flex flex-wrap">
            <div class="my_container-info d-flex">
                <p>{{ title }}</p>
            </div>
            <div>
                <p>{{ original_title }}</p>
            </div>
            <div class="d-flex">
                <p>{{ original_language }}</p> <img :src="`/src/assets/img/png100px/${original_language}.png`" alt="">
            </div>
            <div>{{ vote_average }}</div>
        </div>
    </article>
</template>
       

<script>
export default {
    props: {
        title: 'string',
        original_title: 'string',
        poster_path: 'string',
        original_language: 'string',
        vote_average: 'string',
    },
    data() {
        return {

        }
    },
    methods: {

    }

}
</script>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;
@use '../style/partials/mixins' as *;

article {
    height: 278px;
    width: 185px;
    overflow: hidden;

    &:hover img {
        display: none;
    }

    &:hover div.my_container-info {
        display: flex;
    }


    div.my_container-info {
        height: 100%;
        width: 100%;

        div {
            font-size: 0.5rem
        }
    }
}
</style>