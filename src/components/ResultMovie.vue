<template>
  <div>
    <div class="row my-3" > 
      <div class="col" align="center">
       
      </div>
    </div>
    <div class="row" > 
      <div class="col" >
        <div class="row">
          <div class="col" align="center">
            <img class="w-80" v-bind:src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path"/>
          </div>
        </div>
        <div class="row">
          <div class="col" align="center">
            <div class="mt-1" style="font-size: 25px">
              <label>Avaliação:</label>
              <span class="ml-1">{{movie.vote_average}} / 10</span>
            </div>
          </div>
        </div>
      </div>
      <div class="col">
        <h1>Hoje é um bom dia para ver:</h1>
        <h2>{{movie.title}}</h2>
        <div class="mt-4">
          <label>Data de lançamento: </label> 
          <span class="ml-1">{{dateTranslator(movie.release_date)}}</span>
        </div>
        <div class="mt-2">
          <label>Título original: </label> 
          <span class="ml-1">{{movie.original_title}}</span>
        </div>
        <p class="mt-2" style="text-align: justify">{{movie.overview}}</p>
        <b-button block variant="danger" class="mt-4" v-on:click="restart">Voltar</b-button>
      </div>
    </div>
    
  </div>
</template>

<script>

export default {
  name: 'ResultMovie',
  props: ['movie'],
  data() {
    return {
      
    }
  },
  methods: {
    restart: function (){
      this.$emit('restart')
    },
    dateTranslator: function (date){
      const myArray = date.split("-")
      let ano = myArray[0]
      let mes = myArray[1]
      let dia = myArray[2]
      let newDate = dia + "/" + mes + "/" + ano
      return newDate
    }
  }
}

</script>


<style scoped>
h2 {
  font-size: 30px;
  margin-top: 20px;
  color: #efefef;
}
h1 {
  font-size: 40px
}
img {
  border-radius: 15px
}
label {
  font-weight: bold;
  color: #eeeeee;
}


span, p {
  color: #cccccc;
}

</style>
