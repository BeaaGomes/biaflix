<template>
  <div class="fade-in-image">
    <img src="../assets/biaflix_logo.png" class="img"/>  
  </div>
</template>

<script>
export default {
  name: 'AppTitle',
}
</script>

<style scoped>
.fade-in-image {
  animation: fadeIn 7s;
  -webkit-animation: fadeIn 7s;
  -moz-animation: fadeIn 7s;
  -o-animation: fadeIn 7s;
  -ms-animation: fadeIn 7s;
}

@keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-moz-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-webkit-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-o-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

@-ms-keyframes fadeIn {
  0% {opacity:0;}
  100% {opacity:1;}
}

.img {
  width:50%
}
</style>
