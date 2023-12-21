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
        params: { query: '', language: 'en-US' },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjY2QxYjFmNjliZmFlNWQxZTE4MzQ0NmVmZWZiMTA5YyIsInN1YiI6IjY1ODMwNTYwZTI5NWI0M2JjNzY4NzExNiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.lZNNGkfj6G0PG7Dkrowbcmo9dtKA-R4srQlPpR2-YKI'
        },
      },
      urlTvSeries: {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/tv',
        params: { query: '', language: 'en-US' },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjY2QxYjFmNjliZmFlNWQxZTE4MzQ0NmVmZWZiMTA5YyIsInN1YiI6IjY1ODMwNTYwZTI5NWI0M2JjNzY4NzExNiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.lZNNGkfj6G0PG7Dkrowbcmo9dtKA-R4srQlPpR2-YKI'
        }
      },

      requestedFilms: [],
      requestedTvSeries: [],

    }
  },
  methods: {
    defineSearch(searched) {
      this.urlMovie.params.query = searched
      this.urlTvSeries.params.query = searched
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
    },
    axiosRequestTvSeries() {
      axios.request(this.urlTvSeries)
        .then((response) => {
          this.requestedTvSeries = response.data.results
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
  <AppMain :requestedFilms="requestedFilms" :requestedTvSeries="requestedTvSeries" />
</template>

<style lang="scss">
@use '../src/style/general.scss'
</style>
