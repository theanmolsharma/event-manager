<template>
  <div class="main-cont">
    <Header></Header>
    <NewList :upcomingEventList="upcomingEventList" @openRegForm="openRegForm"></NewList>
    <PastList :pastEventList="pastEventList"></PastList>
    <div class="btn-container">
      <button type="button" class="btn btn-outline-light btn-lg" @click="openEventForm">Add new Event</button>
    </div>
    <RegisterForm v-if="showRegisterForm" :showRegisterForm="showRegisterForm" @closeRegForm="closeRegForm"></RegisterForm>
    <SuccessfulReg v-if="showSuccessfulReg" @closeSuccessReg="closeSuccessReg"></SuccessfulReg>
    <NewEventForm v-if="showNewEventForm" @closeEventForm="closeEventForm" @updateList="updateList"></NewEventForm>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/Header";
import NewList from "./components/NewList";
import PastList from "./components/PastList";
import RegisterForm from "./components/RegisterForm"
import SuccessfulReg from "./components/SuccessfulReg";
import NewEventForm from "./components/NewEventForm";

export default {
  name: 'App',
  components: {NewEventForm, SuccessfulReg, RegisterForm, PastList, NewList, Header},
  data() {
    return {
      upcomingEventList: [],
      pastEventList: [],
      showNewEventForm: false,
      showRegisterForm: false,
      showSuccessfulReg: false,
    }
  },
  created() {
    let outer;
    outer = this;
    axios.get("https://sheetdb.io/api/v1/mtwm963uzgiay").then(response => {
      response.data.forEach(function (item) {
        let d1 = new Date();
        let d2 = new Date(item.Date + " " + item.Time);
        let flag = d1.getTime() < d2.getTime();
        if(flag) {
          outer.upcomingEventList.push(item)
        }
        else {
          outer.pastEventList.push(item)
        }
      });
    });
    console.log(outer.upcomingEventList);
    console.log(outer.pastEventList);
  },
  methods: {
    closeRegForm() {
      this.showRegisterForm = false;
    },
    openRegForm() {
      this.showRegisterForm = true;
    },
    closeSuccessReg() {
      this.showSuccessfulReg = false;
    },
    openEventForm() {
      this.showNewEventForm = true;
    },
    closeEventForm() {
      this.showNewEventForm = false;
    },
    updateList(item) {
      let d1 = new Date();
      let d2 = new Date(item.Date + " " + item.Time);
      let flag = d1.getTime() < d2.getTime();
      if(flag) {
        this.upcomingEventList.push(item)
      }
      else {
        this.pastEventList.push(item)
      }
    }
  }
}
</script>

<style>
.btn-container {
  height: 20vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
.main-cont {
  background-image: linear-gradient(66.47deg, #1C0026 -26.71%, #640685 96.03%);
}
.btn-container button {
  border-radius: 25px;
  padding: 10px 40px 10px;
}
</style>
