<template>
  <div>
    <header>
      <Header @search="searchMoviesAndShows" />
    </header>
    <div class="container">
      <div v-for="movie in moviesData" :key="movie.id">
        <Movie :movieData="movie" />
      </div>
    </div>

    <div class="container">
      <div v-for="show in showsData" :key="show.id">
        <Show :showData="show" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Movie from "./Movie.vue";
import Show from "./Show.vue";

export default {
  name: "Main",
  components: {
    Header,
    Movie,
    Show,
  },
  data() {
    return {
      apiKey: "3fede56bd77f08a65d287138f1c77073",
      searchMoviesUrl: "https://api.themoviedb.org/3/search/movie?",
      searchShowsUrl: "https://api.themoviedb.org/3/search/tv?",
      moviesData: [],
      showsData: [],
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
      this.moviesData = respMovies.results;
      this.showsData = respShows.results;
    },
  },
};
</script>

<style scoped lang="scss">
header {
  background-color: black;
}

.container {
  // padding: 1vh 2vw;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 25px;
}
</style>