<template>
  <div class="form-cont">
    <div class="form p-3" id="form">
      <div class="spacer" style="height: 5vh; width: 100%">
        <button type="button" class="btn btn-outline-danger btn-sm close" @click="closeRegForm">Close</button>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="firstName" type="text" class="effect-1" placeholder="First Name">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="lastName" type="text" class="effect-1" placeholder="Last Name">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="email" type="text" class="effect-1" placeholder="Email Address">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="mobileNumber" type="text" class="effect-1" placeholder="Mobile Number">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <button type="button" class="btn btn-primary btn-lg" @click="submitData">Register</button>
          <span class="Focus-border"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RegisterForm",
  props: ['showRegisterForm'],
  methods: {
    closeRegForm() {
      this.$emit('closeRegForm');
    },
    submitData() {
      var firstName = document.getElementById('firstName').value;
      var lastName = document.getElementById('lastName').value;
      var email = document.getElementById('email').value;
      var mobileNumber = document.getElementById('mobileNumber').value;
      var data = {
        firstName,
        lastName,
        email,
        mobileNumber
      }
      const headers = {
        'Content-Type': 'application/json'
      }
      axios.post("https://sheetdb.io/api/v1/mtwm963uzgiay?sheet=Registered", data, {
        headers: headers
      }).then((response) => console.log(response));
      this.closeRegForm();
    }
  }
}
</script>

<style scoped>
.spacer {
  display: flex;
  justify-content: flex-end;
  align-items: flex-start;
}
.form-cont {
  position: fixed;
  top: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 6;
}
.blur-bg {
  position: relative;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
  background: aliceblue;
  filter: blur(8px);
  -webkit-filter: blur(8px);
}
.form {
  background: white;
  width: 60vw;
  padding: 30px 10px 30px;
  border: 2px solid black;
  z-index: 7;
}

.effect-1
{
  border:0;
  outline: none;
  width: 100%;
  padding: 7px 0;
  border-bottom: 1px solid #ccc ;
}
.effect-1 ~ .Focus-border
{
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: rgb(185,19,185);
  transition: 0.4s;
}
.effect-1:focus ~.Focus-border
{
  width: 100%;
  transition: 0.4s;
  left: 0;
}
.btn1{
  background-color: rgb(185,19,185);
  color: white;
  border-radius: 5px;
  width: 145px;
  outline : none;
  border: none;
  width: 145px;
}
</style>