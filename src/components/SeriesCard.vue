<template>
    <article class="mb-3 overflow-hidden me-1">
        <img class="film-poster_path" :src="coverCreatorSrc(poster_path)" :alt="`${name} cover`">
        <div class="d-flex flex-wrap">
            <div class="my_container-info">
                <div class="d-flex">
                    <p class="fw-bolder me-4">Titolo:</p>
                    <p class="ms-1">{{ name }}</p>
                </div>
                <div class="d-flex">
                    <p class="fw-bolder me-1">Originale:</p>
                    <p class="ms-1">{{ original_name }}</p>
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
                    <p class="ms-1">{{ Math.ceil(vote_average / 2) }} /5</p>
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
        name: 'string',
        original_name: 'string',
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
            return string.slice(0, 120) + '...';
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