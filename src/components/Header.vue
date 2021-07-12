<template>
  <section>
    <form>
      <input v-model="userInput" type="text" />
      <button type="submit">Search</button>
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
  height: 100%;
  padding: 0 1vw;
  display: flex;
  justify-content: flex-end;
  align-items: center;
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