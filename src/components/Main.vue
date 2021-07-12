<template>
  <div>
    <Header />
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
  props: {},
};
</script>

<style scoped lang="scss">
</style>