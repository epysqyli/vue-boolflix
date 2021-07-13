<template>
  <div class="movie-box">
    <p>
      <span>Titolo:</span>
      {{ data.title }}
    </p>
    <p>
      <span>Titolo Originale:</span>
      {{ data.original_title }}
    </p>
    <p class="language">
      Lingua:
      <img
        :src="getFlag(data.original_language)"
        :alt="data.original_language"
      />
    </p>
    <p>Voto: {{ data.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    data: Object,
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
  },
};
</script>

<style scoped lang="scss">
.movie-box {
  border: 1px solid black;
  padding: 10px;
  width: 200px;
  height: fit-content;
  min-height: 250px;

  p {
    margin-bottom: 1vh;
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
}
</style>