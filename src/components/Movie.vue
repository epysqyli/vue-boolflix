<template>
  <div class="box" @mouseover="active = true" @mouseleave="active = false">
    <div class="desc-data" v-show="active">
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

      <div class="vote">
        <span>Voto:</span>
        <div class="stars" v-if="movieData.vote_average != 0">
          <div v-for="n in Math.round(movieData.vote_average / 2)" :key="n.id">
            <font-awesome-icon icon="star" />
          </div>
        </div>
        <div class="stars" v-else>
          <div>-</div>
        </div>
      </div>

      <p class="overview">{{ movieData.overview }}</p>
    </div>

    <div class="poster" v-show="!active">
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
      imagePath: "https://image.tmdb.org/t/p/w342",
      active: false,
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
  width: 350px;
  height: fit-content;
  min-height: 550px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  p {
    span {
      font-weight: bold;
      display: block;
      margin-bottom: 5px;
    }
  }

  .language,
  .vote {
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      width: 50px;
    }

    .stars {
      display: flex;
    }
  }

  .poster {
    img {
      display: block;
      margin: auto;
      width: 342px;
      // max-height: 275px;
    }
  }

  .overview {
    text-align: justify;
  }
}
</style>