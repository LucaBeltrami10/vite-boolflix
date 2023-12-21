<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios'

export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      urlMovie: {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/movie',
        params: { query: '', language: 'en-US', },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjY2QxYjFmNjliZmFlNWQxZTE4MzQ0NmVmZWZiMTA5YyIsInN1YiI6IjY1ODMwNTYwZTI5NWI0M2JjNzY4NzExNiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.lZNNGkfj6G0PG7Dkrowbcmo9dtKA-R4srQlPpR2-YKI'
        }
      },
      requestedFilms: [],

    }
  },
  methods: {
    defineSearch(film) {
      this.urlMovie.params.query = film
      this.axiosRequestMovie()
    },
    axiosRequestMovie() {
      axios.request(this.urlMovie)
        .then((response) => {
          this.requestedFilms = response.data.results
          console.log(response.data.results);
        })
        .catch(function (error) {
          console.error(error);
        });
    }
  }
}

</script>

<template>
  <AppHeader @movieSearched="defineSearch" />
  <AppMain :requestedFilms="requestedFilms" />
</template>

<style lang="scss">
@use '../src/style/general.scss'
</style>
