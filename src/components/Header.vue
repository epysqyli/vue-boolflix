<template>
  <section :class="{ narrow: narrowNavbar }">
    <h1>boolflix</h1>
    <form>
      <input
        v-model="userInput"
        @input="$emit('search', userInput)"
        type="text"
        placeholder="Cerca film e serie TV"
      />
    </form>
  </section>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      userInput: "",
      narrowNavbar: false,
      lastScrollPos: 0,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    // manage navbar height on scroll
    onScroll() {
      const currentPos =
        window.pageYOffset || document.documentElement.scrollTop;
      if (currentPos < 0) {
        return;
      }
      if (Math.abs(currentPos - this.lastScrollPos) < 60) {
        return;
      }
      this.narrowNavbar = currentPos > this.lastScrollPos;
      this.lastScrollPos = currentPos;
    },
  },
};
</script>

<style scoped lang="scss">
section {
  padding: 0 1vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100px;
  transition: 300ms ease all;

  h1 {
    text-transform: uppercase;
    font-size: 2rem;
    font-weight: bold;
    color: red;
  }
}

.narrow {
  height: 50px;
  h1 {
    font-size: 1.5rem;
  }
  opacity: 0.7;
}

form {
  display: flex;
  gap: 1vw;

  * {
    padding: 5px 10px;
    font-size: 1.2rem;
  }

  input {
    width: fit-content;
    transition: width 300ms;
    width: 200px;
    border: none;
    border-bottom: 1px solid red;
    background-color: black;
    color: white;

    &:focus {
      outline: none;
      width: 300px;

      &::placeholder {
        color: white;
      }
    }

    &::placeholder {
      color: gray;
      font-size: 1.1rem;
    }
  }

  button {
    border-radius: 5px;
    border: 1px solid black;

    &:hover {
      box-shadow: 0 0 2px 1px red inset;
    }
  }
}
</style>