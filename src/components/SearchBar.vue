<template>
  <div class="contain-input">
    <input type="text" v-model="data" placeholder="Search...." class="query">
    <hr>
    <div>
      <RenderCards :query="query"/>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import RenderCards from "./RenderCards.vue";

export default {
  name: "SearchBar",
  components: {
    RenderCards
  },
  data() {
    return {
      data: "",
      query: ""
    };
  },
  watch: {
    data() {
      axios
        .get(
          `https://newsapi.org/v2/everything?q=${
            this.data
          }&apiKey=bb099b09ac6a417c8e0bad543fbf0311`
        )
        .then(res => {
          this.query = res.data.articles;
        })
        .catch(err => alert("ERROR!!!"));
    }
  }
};
</script>

<style scoped>
.query {
  margin-bottom: 12px;
  font-size: 21px;
  text-align: center;
  border: none;
  border-color: transparent;
  outline: none;
  font-family: cursive;
}
.query:active,
.query:hover {
  border-bottom: 1px solid #000;
}
</style>
