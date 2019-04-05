<template>
  <header>
    <router-link to="/">
      <h1>{{title}}</h1>
    </router-link>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String
  },
  data() {
    return {
      name: "Dude",
      show: false
    };
  },
  computed: {
    newTitle: function() {
      return this.name;
    }
  }
};
</script>

<style scoped>
header {
  background-color: #222;
  color: #fff;
  padding: 20px;
}
h1 {
  margin: 0;
}
a {
  text-decoration: none;
  color: #fff;
}
</style>
