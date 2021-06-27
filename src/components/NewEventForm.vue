<template>
  <div class="form-cont">
    <div class="form p-3" id="form">
      <div class="spacer" style="height: 6vh; width: 100%">
        <button type="button" class="btn btn-extra btn-outline-danger btn-sm close" @click="closeEventForm">Close</button>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Name" type="text" class="effect-1" placeholder="Name of Event">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Description" type="text" class="effect-1" placeholder="Write a one line description of the event">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Date" type="date" class="effect-1" value="2020-06-27">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Time" type="time" class="effect-1" placeholder="Ex: 3:00 pm">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Duration" type="text" class="effect-1" placeholder="Ex: 3 hours">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Location" type="text" class="effect-1" placeholder="Ex: Lucknow">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <input id="Secret" type="password" class="effect-1" placeholder="Enter Secret Key">
          <span class="Focus-border"></span>
        </div>
      </div>
      <div class="form-row pb-4">
        <div class="col-lg-12">
          <button type="button" class="btn btn-extra btn-primary btn-lg" @click="submitData">Add New Event</button>
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
  methods: {
    closeEventForm() {
      this.$emit('closeEventForm');
    },
    submitData() {
      let Name = document.getElementById('Name').value;
      let Description = document.getElementById('Description').value;
      let Date = document.getElementById('Date').value;
      let Time = document.getElementById('Time').value;
      let Duration = document.getElementById('Duration').value;
      let Location = document.getElementById('Location').value;
      let data = {
        Name,
        Description,
        Date,
        Time,
        Duration,
        Location,
      };
      const headers = {
        'Content-Type': 'application/json'
      }
      let secret = document.getElementById('Secret').value;
      axios.post("https://sheetdb.io/api/v1/"+secret, data, {
        headers: headers
      }).then((response) => {
        console.log(response);
        if(response.status === 201) {
          this.$emit('updateList', data);
        }
      });
      this.closeEventForm();
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