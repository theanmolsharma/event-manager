<template>
  <div class="col-lg-4 col-md-6 col-sm-12">
    <div class="card box-shadow mx-auto my-5" style="width: 18rem;">
      <img src="https://nsa40.casimages.com/img/2021/06/15/210615072119710056.jpg" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Anémone</h5>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        <a href="#" class="btn btn-dark">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewListItem"
}
</script>

<style scoped>
.box-shadow {
  -webkit-box-shadow: 0 1px 1px rgba(72,78,85,.6);
  box-shadow: 0 1px 1px rgba(72,78,85,.6);
  -webkit-transition: all .2s ease-out;
  -moz-transition: all .2s ease-out;
  -ms-transition: all .2s ease-out;
  -o-transition: all .2s ease-out;
  transition: all .2s ease-out;
}

.box-shadow:hover {
  -webkit-box-shadow: 0 20px 40px rgba(72,78,85,.6);
  box-shadow: 0 20px 40px rgba(72,78,85,.6);
  -webkit-transform: translateY(-15px);
  -moz-transform: translateY(-15px);
  -ms-transform: translateY(-15px);
  -o-transform: translateY(-15px);
  transform: translateY(-15px);
}
</style>