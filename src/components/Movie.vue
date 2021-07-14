<template>
  <div class="box">
    <p>
      <span>Titolo:</span>
      {{ movieData.title || movieData.name }}
    </p>

    <p>
      <span>Titolo Originale:</span>
      {{ movieData.original_title || movieData.original_name }}
    </p>

    <p class="language">
      Lingua:
      <img
        :src="getFlag(movieData.original_language)"
        :alt="movieData.original_language"
      />
    </p>

    <p>Voto: {{ Math.round(movieData.vote_average / 2) }}</p>
    <div>
      <font-awesome-icon icon="star" />
    </div>

    <div class="poster">
      <img :src="generateImage(movieData.poster_path)" alt="movie poster" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    movieData: Object,
  },
  data() {
    return {
      imagePath: "https://image.tmdb.org/t/p/w185",
    };
  },

  methods: {
    getFlag(flagCode) {
      try {
        const path = require("../assets/" + flagCode + ".png");
        return path;
      } catch (error) {
        return require("../assets/missing.png");
      }
    },
    generateImage(posterPath) {
      if (posterPath) {
        return `${this.imagePath}${posterPath}`;
      } else {
        return require("../assets/missing_poster.png");
      }
    },
  },
};
</script>

<style scoped lang="scss">
.box {
  background-color: rgba(105, 105, 105, 0.5);
  padding: 10px;
  margin: 1vh 0.5vw;
  border-radius: 12px;
  width: 200px;
  height: fit-content;
  min-height: 600px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;

  p {
    span {
      font-weight: bold;
      display: block;
      margin-bottom: 5px;
    }
  }

  .language {
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      width: 50px;
    }
  }

  .poster {
    img {
      display: block;
      margin: auto;
      width: 185px;
    }
  }
}
</style>