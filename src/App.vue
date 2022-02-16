<template>
  <div id="app">
    <div class="container">
      <Home v-if="state == 0" v-on:category-selected="onCategorySelected"/>
      <Loading v-if="state == 1" v-on:movie-found="onMovieFound" v-bind:category="category"/>
      <ResultMovie v-if="state == 2" v-on:restart="state=0" v-bind:movie="movie"/>
    </div>
  </div>
</template>

<script>
import Home from './components/Home.vue'
import Loading from './components/Loading.vue'
import ResultMovie from './components/ResultMovie.vue'

export default {
  name: 'App', 
  components: {
    Home,
    Loading,
    ResultMovie
  },
  metaInfo: {
      title: 'Biaflix'
  },
  data() {
    return {
      category: null,
      movie: {},
      state: 0
    }
  },
  methods: {
    onCategorySelected: function (category){
      this.category = category
      this.state = 1   
    },
    onMovieFound: function (movie){
      this.movie = movie
      this.state = 2
    }
  },
}
</script>

<style>
body {
  background: #141414 !important;
}
#app {
  color: white;
}
</style>

