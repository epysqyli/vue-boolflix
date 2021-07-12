<template>
  <div id="app">
    <header>
      <Header @search="searchMovies" />
    </header>
    <div class="container">
      <div v-for="movie in movieData" :key="movie.id">
        <Movie :data="movie" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Movie from "./components/Movie.vue";

export default {
  name: "App",
  components: {
    Header,
    Movie,
  },
  data() {
    return {
      apiKey: "3fede56bd77f08a65d287138f1c77073",
      searchMoviesUrl: "https://api.themoviedb.org/3/search/movie?",
      movieData: [],
    };
  },
  methods: {
    async searchMovies(userInput) {
      let resp = await fetch(
        `${this.searchMoviesUrl}api_key=${this.apiKey}&language=it-IT&query=${userInput}`,
        {
          mode: "cors",
        }
      );
      resp = await resp.json();
      this.movieData = resp.results;
    },
  },
};
</script>

<style scoped lang="scss">
@import "./style/common.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

header {
  height: 7vh;
}

.container {
  padding: 1vh 2vw;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 25px;
}
</style>