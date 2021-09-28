<template>
  <div id="app">
    <!-- Perform per ricevere l'informazione dell'header -->
    <Header @performSearch="search" />
    <!-- :movieCards per inviare l'informazione al Main -->
    <Main :movieCards="movies" :seriesCards="series" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "77044b3f5f3cf322ff14c15889b611bc",
      movies: [],
      series: [],
    };
  },
  methods: {
    getMovies(apiParams) {
      axios.get(this.apiUrl + "movie", apiParams).then((response) => {
        this.movies = response.data.results;
      });
    },
    getSeries(apiParams) {
      axios.get(this.apiUrl + "tv", apiParams).then((response) => {
        this.series = response.data.results;
      });
    },
    search(searchText) {
      const paramsObj = {
        params: {
          api_key: this.apiKey,
          query: searchText,
        },
      };
      this.getMovies(paramsObj);
      this.getSeries(paramsObj);
    },
    // fetchApi(query, arr) {
    //   axios
    //     .get(`${this.APIUrl}${this.myApiKey}&query=${query}`)
    //     .then((res) => (this[arr] = res.data.results));
    // },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import "./style/generals";

body {
  background-color: #181818;
}
#app {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
}
</style>
