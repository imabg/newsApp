<template>
  <div>
    <Card :query="query"/>
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "RenderCards",
  components: {
    Card
  },
  props: {
    query: {
      required: true
    }
  }
};
</script>

