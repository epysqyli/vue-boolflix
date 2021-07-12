<template>
  <div>
    <header><Header /></header>
    <Movie />
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
    };
  },
  methods: {
    async searchMovies() {
      let resp = await fetch(
        `${this.searchMoviesUrl}api_key=${this.apiKey}&language=it-IT&query=fast`,
        {
          mode: "cors",
        }
      );
      resp = await resp.json();
      console.log(resp);
    },
  },
  mounted() {
    this.searchMovies();
  }
};
</script>

<style scoped lang="scss">
header {
  height: 7vh;
  border: 1px solid red;
}
</style>