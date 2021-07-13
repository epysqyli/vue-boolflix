<template>
  <div class="movie-box">
    <p>
      Titolo:<br />
      {{ data.title }}
    </p>
    <p>
      Titolo Originale:<br />
      {{ data.original_title }}
    </p>
    <p class="language">Lingua: <img src="../assets/en.png" alt="" /></p>
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