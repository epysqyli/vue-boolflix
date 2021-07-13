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
    <p class="language">Lingua: <img :src="require('../assets/' + data.original_language + '.png')" :alt="data.original_language" /></p>
    <p>Voto: {{ data.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    data: Object,
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