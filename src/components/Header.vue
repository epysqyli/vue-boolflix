<template>
  <section>
    <div>
      <input v-model="userInput" type="text" />
    </div>
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
</style>