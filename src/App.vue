<script>
import axios from 'axios'
import { store } from './components/data/store'
import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue';
export default {
  name: 'App',
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
      apiKey: '3804462719384461f507b7cd3f30d4e5',
      moviesApiUri: 'https://api.themoviedb.org/3/search/movie?',
      seriesApiUri: 'https://api.themoviedb.org/3/search/tv?'

    }
  },
  methods: {
    getMovies(searchTitle) {

      axios.get(this.moviesApiUri, {
        params: {
          api_key: this.apiKey,
          query: searchTitle,

        }
      })
        .then((res) => {

          this.store.movies = res.data.results;

        })
    },
    getSeries(searchTitle) {
      console.log(searchTitle);
      axios.get(this.seriesApiUri, {
        params: {
          api_key: this.apiKey,
          query: searchTitle,

        }
      })
        .then((res) => {

          this.store.series = res.data.results;

        })
    },
    searchAll(searchTitle) {
      this.getMovies(searchTitle);
      this.getSeries(searchTitle)
    }

  }
}
</script>

<template>

  <AppHeader @research="searchAll"></AppHeader>
  <AppMain></AppMain>
</template>

<style>

</style>