<template>
  <div>
    <header><Header /></header>
    <div class="container">
      <div v-for="movie in movieData" :key="movie.id">
        <Movie :data="movie" />
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
      movieData: [],
    };
  },
  methods: {
    async searchMovies() {
      let resp = await fetch(
        `${this.searchMoviesUrl}api_key=${this.apiKey}&language=it-IT&query=potter`,
        {
          mode: "cors",
        }
      );
      resp = await resp.json();
      this.movieData = resp.results;
      console.log(this.movieData);
    },
  },
  mounted() {
    this.searchMovies();
  },
};
</script>

<style scoped lang="scss">
header {
  height: 7vh;
  border: 1px solid red;
}

.container {
  padding: 1vh 2vw;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 25px;
}
</style>