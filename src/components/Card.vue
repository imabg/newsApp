<template>
  <div class="container">
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="(article, index) in query" :key="index">
        <a :href="article.url" target="_blank">
          <div class="card">
            <div class="card-image">
              <figure class="image is-3by2">
                <img :src="article.urlToImage" :alt="article.title">
              </figure>
            </div>
            <div class="card-content">
              <div class="content">{{ article.title }}</div>
            </div>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    query: {
      required: true
    }
  },
  data() {
    return {
      articles: ""
    };
  }
};
</script>

<style scoped>
.card {
  margin: 5px;
  border: 1px solid #000;
}
.card:hover,
.card:active {
  cursor: pointer;
  background: #e3e3e3;
}
</style>
