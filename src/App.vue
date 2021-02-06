<template>
  <div id="app">
    <h1>Éditeur rich text</h1>
    <div class="card shadow my-3" id="post-create">
      <label for="post-body">Article</label>
      <post-add-body></post-add-body>
    </div>
  </div>
</template>

<script>
import PostAddBody from "./components/PostAddBody.vue";

export default {
  name: "App",
  components: {
    PostAddBody,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  .card {
    min-width: 60vw;
    max-width: 95vw;
    margin: auto auto;
  }

  iframe, .post-text {
    width: 100%;
    height: 30vw;
  }

  .post-text {
    text-align: left;
  }
}
</style>
