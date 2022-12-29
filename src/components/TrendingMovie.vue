<template>
  <div id="example">
    <h2 class="mx-3 grey--text">
      Trending Movies
    </h2>
    <carousel-3d :controls-visible="true" :clickable="false" :key="trendingMovies.length" :listData="trendingMovies" :height="350">
      <slide :index="i" :key="i" v-for="(movie, i) in this.trendingMovies">
        <figure>
          <img :src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" />
          <figcaption>
            <v-btn :to="`/movie/${movie.id}`" text color="white"> {{ movie.title }}</v-btn>
          </figcaption>
        </figure>
      </slide>
    </carousel-3d>
  </div>
</template>

<script>
import { Carousel3d, Slide } from 'vue-carousel-3d';
export default {
  data() {
    return {
      trendingMovies: [],
    };
  },
  components: {
    Carousel3d,
    Slide,
  },
  mounted() {
    this.fetchtrendingMovies();
  },
  methods: {
    async fetchtrendingMovies() {
      const response = await this.$http.get('https://api.themoviedb.org/3/trending/all/day?api_key=bb6f51bef07465653c3e553d6ab161a8');

      this.trendingMovies = response.data.results.slice(1, 6);
      console.log(this.trendingMovies);
    },
  },
};
</script>

<style>
.carousel-3d-container figure {
  margin: 0;
}

.carousel-3d-container figcaption {
  position: absolute;
  background-color: rgba(0, 0, 0, 0.5);
  color: black;
  bottom: 0;
  position: absolute;
  bottom: 0;
  padding: 15px;
  font-size: 12px;
  min-width: 50%;
  box-sizing: border-box;
}

.next span,
.prev span {
  color: red;
}
</style>
