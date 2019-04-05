<template>
  <header>
    <router-link to="/">
      <h1>{{title}}</h1>
      <transition name="fade">
        <h1 v-if="show">Animation</h1>
      </transition>
      <button @click="show = !show">Toggle</button>
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
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s ease;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: scale(0);
}
</style>
