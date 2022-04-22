<template>
  <header>
    <img id="logo" src="../assets/logo.png" alt="Netflix Logo" />
    <div>
      <input
        v-model="textToSearch"
        type="text"
        placeholder="Cerca Film o Serie TV"
      />
      <button @click="search">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      textToSearch: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.textToSearch);
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  height: 8vh;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 5px;
  color: red;
  background-color: black;
  img {
    width: 100px;
  }
  input {
    height: 30px;
    padding: 0 5px;
    border-radius: 5px;
  }
  button {
    height: 25px;
    background-color: white;
    border: 0;
    border-radius: 5px;
  }
}
</style>