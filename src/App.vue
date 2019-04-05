<template>
  <div id="app">
    <Header :title="title" v-if="isTrue"/>
    <MovieList/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import MovieList from "./components/MovieList.vue";

export default {
  name: "app",
  components: {
    Header,
    MovieList
  },
  data: () => ({
    title: "Vue Movie DB",
    isTrue: true
  })
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
