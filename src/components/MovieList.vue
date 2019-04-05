<template>
  <div>{{movie.title}}</div>
</template>

<script>
/**
 * @API - The Movie DB
 * @key - ab1108ff64d84d869773eb7692b0749f
 * @Root_url - https://api.themoviedb.org
 * @example - https://api.themoviedb.org/3/movie/550?api_key=${key}
 */

const API = {
  key: "ab1108ff64d84d869773eb7692b0749f",
  root_url: "https://api.themoviedb.org",
  discover: "discover/movie?sort_by=popularity.desc"
};
export default {
  name: "MovieList",
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
      const randomPage = max => Math.floor(Math.random() * Math.floor(max));
      try {
        const url = "".concat(
          `${API.root_url}/3/${API.discover}&api_key=${
            API.key
          }&page=${randomPage(10)}`
        );
        const res = await fetch(url);
        const movie = await res.json();
        this.movie = movie;
      } catch (error) {
        throw new Error(error);
      }
    }
  }
};
</script>

<style>
</style>
