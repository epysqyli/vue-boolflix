<template>
  <div class="box">
    <p>
      <span>Titolo:</span>
      {{ showData.name }}
    </p>
    <p>
      <span>Titolo Originale:</span>
      {{ showData.original_name }}
    </p>
    <p class="language">
      Lingua:
      <img
        :src="getFlag(showData.original_language)"
        :alt="showData.original_language"
      />
    </p>
    <p>Voto: {{ showData.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    showData: Object,
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
  border: 1px solid black;
  padding: 10px;
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