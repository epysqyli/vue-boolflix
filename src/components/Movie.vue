<template>
  <div class="box" @mouseover="active = true" @mouseleave="active = false">
    <div class="desc-data" v-show="active">
      <p class="title">
        {{ movieData.title || movieData.name }}
      </p>

      <p class="original-title">
        <span>Titolo Originale:</span>
        <span>{{ movieData.original_title || movieData.original_name }}</span>
      </p>

      <div class="additional-info">
        <img
          :src="getFlag(movieData.original_language)"
          :alt="movieData.original_language"
        />
        <div class="stars">
          <template v-if="movieData.vote_average != 0">
            <div
              v-for="n in Math.round(movieData.vote_average / 2)"
              :key="n.id"
            >
              <font-awesome-icon icon="star" />
            </div>
          </template>
          <template v-else>
            <div> - </div>
          </template>
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
  width: 345px;
  min-height: 500px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: transform 300ms;

  &:hover {
    transform: scale(1.04);
    box-shadow: 0 0 5px 2px whitesmoke;
  }

  .title {
    font-size: 1.5rem;
    text-align: center;
    text-transform: uppercase;
    font-weight: bold;
    color: white;
    font-family: monospace;
  }

  .original-title {
    font-size: 0.9rem;
    display: flex;
    justify-content: space-between;
    color: rgb(225, 225, 225);
  }

  .additional-info {
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      width: 100px;
    }
  }

  .stars {
    display: flex;
    color: white;
    gap: 5px;
  }

  .poster {
    img {
      display: block;
      border-radius: 10px;
      margin: auto;
      width: 342px;
      max-height: 500px;
      object-fit: cover;
    }
  }

  .overview {
    text-align: justify;
    font-size: 0.9rem;
    color: rgb(225, 225, 225);
  }
}
</style>