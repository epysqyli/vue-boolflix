<template>
  <div class="movie-box">
    <p>Titolo: {{ data.title }}</p>
    <p>Titolo Originale: {{ data.original_title }}</p>
    <p>Lingua: {{ data.original_language }}</p>
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
  }
}
</style>