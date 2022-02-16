<template>
  <div>
    <div class="row" style="margin-top: 100px;"> 
      <div class="col" align="center">
        <img src="../assets/popcorn.gif" style="width:95%"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Loading',
  props: ['category'],
  data() {
    return {
    }
  },
  created: function () {
    let result = null;
    let responseTooSlow = false;

    setTimeout(() => {
      if(result){
        this.$emit('movie-found', result)
      } else {
        responseTooSlow = true;
      }
    }, 1700)

    let page = Math.floor(Math.random() * 10) + 1
    this.axios.get("https://api.themoviedb.org/3/discover/movie?api_key=caba9ccc8fe706b0aace2a40d925f39f&language=pt-BR&sort_by=popularity.desc&include_adult=true&include_video=false&page=" + page + "&with_genres=" + this.category).then((response) => {
      let movie = Math.floor(Math.random() * 20)
      result = response.data.results[movie]
      if (responseTooSlow){
        this.$emit('movie-found', result)
      } 
    })  
  }
}
</script>
