<template>
  <div id="app">
    <Header @research="researchValue" />
    <Main />
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
      myApiKey: "77044b3f5f3cf322ff14c15889b611bc",
      APIUrl: "https://api.themoviedb.org/3/movie/550?api_key=",
    };
  },
  methods: {
    fetchApi(query, arr) {
      axios
        .get(`${this.APIUrl}${this.myApiKey}&query=${query}`)
        .then((res) => (this[arr] = res.data.results));
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import "./style/generals";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
}
</style>
