<template>
  <section>
    <h1>boolflix</h1>
    <form>
      <input v-model="userInput" type="text" />
      <button @click.prevent="$emit('search', userInput)" type="submit">
        Search
      </button>
    </form>
  </section>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      userInput: "",
    };
  },
};
</script>

<style scoped lang="scss">
section {
  padding: 0 1vw;
  display: flex;
  justify-content: space-between;
  align-items: center;

  h1 {
    text-transform: uppercase;
    font-size: 2rem;
    font-weight: bold;
    color: red;
  }
}

form {
  display: flex;
  gap: 1vw;

  * {
    padding: 5px 10px;
    font-size: 1.2rem;
  }
}
</style>