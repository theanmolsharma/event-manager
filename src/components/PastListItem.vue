<template>
  <div class="col-lg-4 col-md-6 col-sm-12">
    <div class="card box-shadow mx-auto my-5" style="width: max(25vw, 20rem);">
      <img src="https://nsa40.casimages.com/img/2021/06/15/210615072119710056.jpg" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title mt-1 md-1">{{event.Name}}</h5>
        <h6 class="card-subtitle mt-1 md-1">{{event.Date}} - {{event.Time}}</h6>
        <h6 class="card-subtitle mt-1 md-1">{{event.Duration}}</h6>
        <h6 class="card-subtitle mt-1 md-1">{{event.Location}}</h6>
        <p class="card-text mt-1 md-1">{{event.Description}}</p>
        <p></p>
        <button class="btn btn-outline-dark btn-lg" disabled>Register</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PastListItem",
  props: ['event']
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