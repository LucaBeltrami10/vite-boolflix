<template>
    <article class="mb-3 overflow-hidden me-1">
        <!--  :src="`https://image.tmdb.org/t/p/w185/${poster_path}`"  -->
        <img class="film-poster_path" src="../assets/img/not-available.png" :alt="`${title} cover`">
        <div class="d-flex flex-wrap">
            <div class="my_container-info">
                <div class="d-flex">
                    <p class="fw-bolder">Titolo:</p>
                    <p class="ms-1">{{ title }}</p>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder">Originale:</p>
                    <p class="ms-1">{{ original_title }}</p>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder">Lingua:</p>
                    <div class="container-language-flag ms-1">
                        <p>{{ original_languag }}</p>
                        <img class="language-flag" :src="`/src/assets/img/png100px/${original_language}.png`" alt="">
                    </div>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder">Voto:</p>
                    <p class="ms-1">{{ Math.ceil(vote_average / 2) }} /5</p>
                </div>
            </div>
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
    color: white;
    font-size: 0.8rem;

    &:hover img.film-poster_path {
        display: none;
    }

    &:hover div.my_container-info {
        display: block;
    }


    div.my_container-info {
        height: 100%;
        width: 100%;

        div.container-language-flag {
            height: 15px;
            position: relative;

            p {
                position: absolute;
                z-index: 1;
            }

            img.language-flag {
                height: 100%;
                z-index: 2;
            }
        }
    }


}
</style>