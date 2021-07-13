<template>
  <div class="box">
    <p>
      <span>Titolo:</span>
      {{ movieData.title }}
    </p>
    <p>
      <span>Titolo Originale:</span>
      {{ movieData.original_title }}
    </p>
    <p class="language">
      Lingua:
      <img
        :src="getFlag(movieData.original_language)"
        :alt="movieData.original_language"
      />
    </p>
    <p>Voto: {{ movieData.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    movieData: Object,
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
.box {
  background-color: rgba(105, 105, 105, 0.5);
  padding: 10px;
  margin: 1vh 0.5vw;
  border-radius: 12px;
  width: 200px;
  height: fit-content;
  min-height: 275px;

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