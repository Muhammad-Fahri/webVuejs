<template>
   <div>
    <TrendingMovie />
     <PopularMovies />
     <TopRatedMovies />
     <UpcomingMovies />
   </div>
</template>

<script>
  
import TopRatedMovies from '../components/TopRatedMovies.vue'
import PopularMovies from '../components/PopularMovies.vue'
import UpcomingMovies from '../components/UpcomingMovies.vue'
import TrendingMovie from '../components/TrendingMovie.vue'
  export default {
    name: 'Home',
    components: {
    TrendingMovie,
    PopularMovies,
    TopRatedMovies,
    UpcomingMovies
    }

    
  }
</script>
