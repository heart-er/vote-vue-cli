<template>
  <div id="app">
    <h2 class="title has-text-centered dividing-header">UpVote!</h2>
    <div class="section">
      <submission ></submission>
    </div>
  </div>
</template>

<script>
import submission from "./components/submission";
export default {
  name: "app",
  components: {
    submission
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
.section {
  padding: 2rem 1.5rem;
}
</style>
