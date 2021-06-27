<template>
  <div class="col-lg-4 col-md-6 col-sm-12">
    <div class="card box-shadow mx-auto my-5" style="width: max(25vw, 20rem);">
      <div class="card-body">
        <h5 class="card-title mt-3 md-2">{{event.Name}}</h5>
        <h6 class="card-subtitle mt-1 md-1">{{event.Date}} - {{event.Time}}</h6>
        <h6 class="card-subtitle mt-1 md-1">{{event.Duration}}</h6>
        <h6 class="card-subtitle mt-1 md-1">{{event.Location}}</h6>
        <p class="card-text mt-1 md-1">{{event.Description}}</p>
        <button type="button" class="btn-extra btn btn-outline-light btn-lg" @click="openRegForm">Register</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewListItem",
  props: ['event'],
  methods: {
    openRegForm() {
      this.$emit('openRegForm');
    }
  }
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

.card {
  /*background: linear-gradient(225deg, #00c6ff, #0072ff);*/
  outline: none;
  border: none;
  border-radius: 5vh;
  background-image: url("../assets/Card-1.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 45vh;
}

.card-body {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;

  text-align: center;
  color: white;
}

.card-title {
  font-size: 30px;
  line-height: 36px;

  color: #FFFFFF;
}

.btn-extra {
  border-radius: 40px;
}
</style>