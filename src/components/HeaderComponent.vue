<template>
  <header>
    <div class="navigation">
      <div>
        <img
          id="logo"
          src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png"
          alt="Netflix Logo"
        />
      </div>
      <div>
        <ul>
          <li>
            <a href="#">Home</a>
          </li>
          <li>
            <a href="#">Serie TV</a>
          </li>
          <li>
            <a href="#">Film</a>
          </li>
          <li>
            <a href="#">Originali</a>
          </li>
          <li>
            <a href="#">Aggiunti di recente</a>
          </li>
          <li>
            <a href="#">La mia lista</a>
          </li>
        </ul>
      </div>
    </div>

    <div class="search-section">
      <input
        class="margin-10"
        v-model="textToSearch"
        type="text"
        placeholder="Cerca Film o Serie TV"
      />
      <button class="margin-10" @click="search">
        <i class="fa-solid fa-magnifying-glass"></i>
      </button>
      <p class="margin-10">BAMBINI</p>
      <i class="fa-solid fa-bell margin-10"></i>
      <img class="margin-10" src="../assets/Netflix-avatar.png" alt="avatar" />
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
      if (this.textToSearch != "") {
        this.$emit("search", this.textToSearch.trim());
      }
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
  color: lightgrey;
  background-color: #333;
  img {
    width: 100px;
  }
  .navigation {
    display: flex;
    align-items: center;
    img {
      margin: 0 15px;
    }
    ul {
      list-style: none;
      li {
        display: inline-block;
        margin: 0 10px;
        font-weight: 600;
        a {
          color: lightgrey;
          text-decoration: none;
        }
        a:hover {
          color: white;
        }
      }
    }
  }
  .search-section {
    display: flex;
    align-items: center;
    img {
      width: 40px;
    }
    input {
      height: 25px;
      width: 150px;
      padding: 0 5px;
      border-radius: 5px;
      border: 0;
      background-color: transparent;
      color: lightgray;
    }
    button {
      height: 25px;
      background-color: transparent;
      border: 0;
      color: white;
      font-size: 18px;
    }
  }
  .margin-10 {
    margin-right: 10px;
  }
}
</style>