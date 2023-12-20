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
      lookedFor: "",
      options: {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/movie',
        params: { query: '', include_adult: 'false', language: 'en-US', page: '1' },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjY2QxYjFmNjliZmFlNWQxZTE4MzQ0NmVmZWZiMTA5YyIsInN1YiI6IjY1ODMwNTYwZTI5NWI0M2JjNzY4NzExNiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.lZNNGkfj6G0PG7Dkrowbcmo9dtKA-R4srQlPpR2-YKI'
        }
      },
      axiosResponse: [],

    }
  },
  methods: {
    defineSearch(film) {
      this.lookedFor = film;
      this.axiosRequest()
    },
    axiosRequest() {
      axios.request(this.options)
        .then((response) => {
          this.axiosResponse = response
          console.log(response.data);
        })
        .catch(function (error) {
          console.error(error);
        });
    }
  }
}

</script>

<template>
  <AppHeader @moviesearched="defineSearch" />
  <AppMain :lookedFor="lookedFor" :axiosResponse="axiosResponse" />
</template>

<style scoped></style>
