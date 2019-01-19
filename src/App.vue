<template>
  <div>
    <SectionApp/>
    <div id="app">
      <SearchBar/>
      <div v-show="statusOk">
        <RenderCards :query="query"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SectionApp from "./components/SectionApp.vue";
import SearchBar from "./components/SearchBar.vue";
import RenderCards from "./components/RenderCards.vue";

export default {
  name: "app",
  components: {
    SectionApp,
    SearchBar,
    RenderCards
  },
  data() {
    return {
      statusOk: false,
      query: ""
    };
  },
  beforeMount() {
    axios
      .get(
        `
https://newsapi.org/v2/top-headlines?country=us&apiKey=bb099b09ac6a417c8e0bad543fbf0311`
      )
      .then(res => {
        this.query = res.data.articles;
        this.statusOk = true;
      })
      .catch(err => alert("ERROR!!!"));
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
