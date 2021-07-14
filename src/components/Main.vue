<template>
  <div>
    <header>
      <Header @search="searchMoviesAndShows" />
    </header>
    <div class="container">
      <div v-for="movie in moviesAndShowsData" :key="movie.id">
        <Movie :movieData="movie" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Movie from "./Movie.vue";

export default {
  name: "Main",
  components: {
    Header,
    Movie,
  },
  data() {
    return {
      apiKey: "3fede56bd77f08a65d287138f1c77073",
      searchMoviesUrl: "https://api.themoviedb.org/3/search/movie?",
      searchShowsUrl: "https://api.themoviedb.org/3/search/tv?",
      moviesAndShowsData: [],
    };
  },
  methods: {
    async searchMoviesAndShows(userInput) {
      let respMovies = await fetch(
        `${this.searchMoviesUrl}api_key=${this.apiKey}&language=it-IT&query=${userInput}`,
        {
          mode: "cors",
        }
      );
      let respShows = await fetch(
        `${this.searchShowsUrl}api_key=${this.apiKey}&language=it-IT&query=${userInput}`,
        {
          mode: "cors",
        }
      );
      respMovies = await respMovies.json();
      respShows = await respShows.json();
      this.moviesAndShowsData = [...respMovies.results, ...respShows.results];
    },
  },
};
</script>

<style scoped lang="scss">
header {
  background-color: black;
  position: fixed;
  width: 100%;
}

.container {
  padding-top: 10vh;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 25px;
}
</style>