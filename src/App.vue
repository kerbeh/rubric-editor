<template>
  <div id="app" class="container">

    <Rubric></Rubric>
  </div>
</template>

<script>
import Rubric from "./components/Rubric.vue";

export default {
  name: "app",
  components: {
    Rubric
  }
};
</script>

<style lang="less" scoped>
@import "../node_modules/bootstrap3/less/bootstrap.less";

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
