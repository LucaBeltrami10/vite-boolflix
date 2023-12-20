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

    }
  },
  methods: {
    defineSearch(film) {
      this.lookedFor = film
    }
  }
}

</script>

<template>
  <AppHeader @moviesearched="defineSearch" />
  <AppMain :lookedFor="lookedFor" />
</template>

<style scoped></style>
