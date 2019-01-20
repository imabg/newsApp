<template>
  <div class="container">
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="(article, index) in query" :key="index">
        <div class="card">
          <div class="card-image">
            <figure class="image is-3by2">
              <img :src="article.urlToImage" :alt="article.title">
            </figure>
          </div>
          <div class="card-content">
            <div class="content">{{ article.title }}</div>
            <a :href="article.url" class="link" target="_blank">Full news</a>
          </div>
        </div>
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
  background: #e3e3e3;
}
.link {
  color: brown;
}
.link:hover,
.link:active {
  text-decoration: underline;
  border: 1px solid #000;
  background-color: #000;
  color: #fff;
  border-radius: 200px;
  padding: 12px;
}
</style>
