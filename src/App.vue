<template>
  <div id="app">
    <h1>Éditeur de texte enrichi</h1>
    <div class="card">
      <label for="post-body">Article 1</label>
      <post-add-body :edit="true"></post-add-body>
    </div>
    <div class="card">
      <label for="post-body">Article 2</label>
      <post-add-body :edit="false"></post-add-body>
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
    max-width: 60vw;
    min-width: 300px;
    margin: 30px auto;

    label {
      font-size: 1.4rem;
    }
  }

  iframe, .post-text {
    width: 100%;
    height: 20vw;
  }

  .post-text {
    font-size: 1.2rem;
    text-align: left;
    border: 1px solid silver;
    padding: 20px;
    margin-bottom: 20px;
  }
}
</style>
