<template>
    <article class="mb-3 overflow-hidden me-1">
        <img class="film-poster_path" :src="coverCreatorSrc(poster_path)" :alt="`${title} cover`">
        <div class="d-flex flex-wrap">
            <div class="my_container-info">
                <div class="d-flex">
                    <p class="fw-bolder me-4">Titolo:</p>
                    <p class="ms-1">{{ title }}</p>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder me-1">Originale:</p>
                    <p class="ms-1">{{ original_title }}</p>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder me-1">Lingua:</p>
                    <div class="container-language-flag ms-1">
                        <p>{{ original_languag }}</p>
                        <img class="language-flag" :src="`/src/assets/img/png100px/${original_language}.png`" alt="">
                    </div>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder me-1">Voto:</p>
                    <!-- <p class="ms-1">{{ Math.ceil(vote_average / 2) }} /5</p> -->
                    <img v-for="el in baseRatingFive(vote_average)" class="rating-star" src="../assets/img/red-star.png"
                        alt="red star">

                </div>
                <div class="d-flex">
                    <p class="ms-1">{{ cutOverview(overview) }}</p>
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
        overview: 'string'
    },
    data() {
        return {

        }
    },
    methods: {
        coverCreatorSrc(path) {
            if (path == null) {
                return '/src/assets/img/not-available.png';
            } else {
                return 'https://image.tmdb.org/t/p/w185/' + path
            }
        },
        cutOverview(string) {
            if (string == '') {
                return ''
            } else {
                return string.slice(0, 120) + '...';
            }
        },
        baseRatingFive(num) {
            return Math.ceil(num / 2);
        },
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
    font-size: 0.75rem;
    overflow: scroll;

    &:hover img.film-poster_path {
        display: none;
    }

    &:hover div.my_container-info {
        display: block;
    }

    div.my_container-info {
        height: 100%;
        width: 100%;

        img.rating-star {
            height: 15px;
        }

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

