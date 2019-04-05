<template>
  <transition name="fade">
    <div class="movie__container" :style="styles">
      <div class="movie__info">
        <h1>{{movie.title}}</h1>
        <h3>Release Date: {{movie.release_date}}</h3>
        <p>{{movie.overview}}</p>
      </div>
    </div>
  </transition>
</template>

<script>
import { API } from "./MovieList.vue";
export default {
  name: "MovieDetails",
  data() {
    return {
      movie: {}
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const url = "".concat(
          `${API.root_url}/3/movie/${this.$route.params.id}?api_key=${API.key}`
        );
        const res = await fetch(url);
        const movie = await res.json();
        this.movie = movie;
      } catch (error) {
        throw new Error(error);
      }
    }
  },
  computed: {
    styles() {
      return {
        background: `url(${API.backdrop_path}/${
          this.movie.backdrop_path
        }) no-repeat`
      };
    }
  }
};
</script>

<style scoped>
.movie__container {
  position: relative;
  padding-top: 50vh;
  background-size: cover !important;
}
.movie__info {
  background: #222;
  padding: 2rem 10%;
}
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s ease;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>
