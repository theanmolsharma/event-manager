<template>
  <div class="form-cont blur-bgimage">
    <div class="form p-3" id="form">
      <div class="spacer" style="height: 6vh; width: 100%">
        <button type="button" class="btn btn-outline-danger btn-sm close btn-extra" @click="closeRegForm">Close</button>
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
          <button type="button" class="btn btn-extra btn-primary btn-lg" @click="submitData">Register</button>
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
  props: ['eventName'],
  methods: {
    closeRegForm() {
      this.$emit('closeRegForm');
    },
    submitData() {
      let firstName = document.getElementById('firstName').value;
      let lastName = document.getElementById('lastName').value;
      let email = document.getElementById('email').value;
      let mobileNumber = document.getElementById('mobileNumber').value;
      let event = this.eventName;
      let data = {
        firstName,
        lastName,
        email,
        mobileNumber,
        event
      }
      console.log(data);
      const headers = {
        'Content-Type': 'application/json'
      }
      axios.post("https://sheetdb.io/api/v1/mtwm963uzgiay?sheet=Registered", data, {
        headers: headers
      }).then((response) => {
        console.log(response.data)
      });
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
.spacer button {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
}
.form-cont {
  position: fixed;
  background-image: linear-gradient(66.47deg, #120d4f, #5e12ce);
  top: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 6;
}
.form {
  background: white;
  width: 60vw;
  padding: 30px 10px 30px;
  border: 2px solid black;
  border-radius: 40px;
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
.btn-extra {
  border-radius: 20px;
}
.form-row {
  margin-left: 20px;
  margin-right: 20px;
}
</style>