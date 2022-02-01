<template>
  <div>
    <div class="row" style="margin-top: 200px;"> 
      <div class="col" align="center">
        <app-title/>
      </div>
    </div>
    <div class="row" style="margin-top: 100px;"> 
      <div class="col fade-in" align="right">
        <label class="form-input">Escolha a categoria:</label>
      </div>
      <div class="col fade-in-slow" align="left">
        <b-form-select v-model="selected_category" :options="categories" class="form-select mt-3"></b-form-select>
        <b-button variant="danger" class="mt-3 ml-2" v-on:click="submitCategory">OK</b-button>
      </div>
    </div>
    
  </div>
</template>

<script>
import AppTitle from './AppTitle.vue'
export default {
  name: 'Home',
  components: {
    AppTitle
  },
  data() {
    return {
      selected_category: null,
      categories: []
    }
  },
  methods: {
    submitCategory: function () {
      this.$emit('category-selected', this.selected_category);
    },
    adaptCategories: function (genres){
      let result = []
      genres.forEach(genre => {
        result.push({value: genre.id, text: genre.name})
      });
      return result    
    }
  },
  created: function () {     
    this.axios.get("https://api.themoviedb.org/3/genre/movie/list?api_key=caba9ccc8fe706b0aace2a40d925f39f&language=pt-BR").then((response) => {
      this.categories = this.adaptCategories(response.data.genres)      
    })
  }
}


</script>


<style scoped>
.form-input{
  font-size: 40px;
}
.form-select{
  width: 50%;
}

.fade-in {
  animation: fadeIn 5s;
  -webkit-animation: fadeIn 5s;
  -moz-animation: fadeIn 5s;
  -o-animation: fadeIn 5s;
  -ms-animation: fadeIn 5s;
}

.fade-in-slow {
  animation: fadeIn 6s;
  -webkit-animation: fadeIn 6s;
  -moz-animation: fadeIn 6s;
  -o-animation: fadeIn 6s;
  -ms-animation: fadeIn 6s;
}

@keyframes fadeIn {
  0% {opacity:0;}
  60% {opacity:0;}
  100% {opacity:1;}
}

@-moz-keyframes fadeIn {
  0% {opacity:0;}
  60% {opacity:0;}
  100% {opacity:1;}
}

@-webkit-keyframes fadeIn {
  0% {opacity:0;}
  60% {opacity:0;}
  100% {opacity:1;}
}

@-o-keyframes fadeIn {
  0% {opacity:0;}
  60% {opacity:0;}
  100% {opacity:1;}
}

@-ms-keyframes fadeIn {
  0% {opacity:0;}
  70% {opacity:0;}
  100% {opacity:1;}
}

</style>
