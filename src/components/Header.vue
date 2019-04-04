<template>
  <header>
    <h1>{{title}}</h1>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String
  }
};
</script>

<style scoped>
header {
  background-color: #111;
  padding: 20p;
  color: #fff;
}
h1 {
  margin: 0;
}
</style>
