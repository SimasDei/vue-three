<template>
  <ul>
    <li v-for="movie in movies" :key="movie.title">
      <Movie :movie="movie"/>
    </li>
  </ul>
</template>

<script>
import Movie from "./Movie";

export const API = {
  key: "ab1108ff64d84d869773eb7692b0749f",
  root_url: "https://api.themoviedb.org",
  discover: "discover/movie?sort_by=popularity.desc",
  backdrop_path: "http://image.tmdb.org/t/p/w1280"
};
export default {
  name: "MovieList",
  data() {
    return {
      movies: []
    };
  },
  beforeCreate: function() {
    console.log("before create");
  },
  created: function() {
    console.log("created");
    this.fetchData();
  },
  beforeMount() {
    console.log("before mount");
  },
  mounted() {
    console.log("mounted");
  },
  beforeUpdate() {
    console.log("before update");
  },
  updated() {
    console.log("updated");
  },
  methods: {
    fetchData: async function() {
      const randomPage = max => Math.floor(Math.random() * Math.floor(max) + 1);
      try {
        const url = "".concat(
          `${API.root_url}/3/${API.discover}&api_key=${
            API.key
          }&page=${randomPage(10)}`
        );
        const res = await fetch(url);
        const movies = await res.json();
        this.movies = movies.results;
      } catch (error) {
        throw new Error(error);
      }
    }
  },
  components: {
    Movie
  }
};
</script>

<style scoped>
ul {
  display: grid;
  list-style: none;
  padding: 1rem;
  margin: 0;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(5, 1fr);
}
</style>
