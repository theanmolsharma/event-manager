<template>
  <div>
    <Header></Header>
    <NewList :upcomingEventList="upcomingEventList" @openRegForm="openRegForm"></NewList>
    <PastList :pastEventList="pastEventList"></PastList>
    <div class="btn-container">
      <button type="button" class="btn btn-outline-dark btn-lg">Add new Event</button>
    </div>
    <RegisterForm v-if="showRegisterForm" :showRegisterForm="showRegisterForm" @closeRegForm="closeRegForm"></RegisterForm>
    <SuccessfulReg v-if="showSuccessfulReg" @closeSuccessReg="closeSuccessReg"></SuccessfulReg>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/Header";
import NewList from "./components/NewList";
import PastList from "./components/PastList";
import RegisterForm from "./components/RegisterForm"
import SuccessfulReg from "./components/SuccessfulReg";
export default {
  name: 'App',
  components: {SuccessfulReg, RegisterForm, PastList, NewList, Header},
  data() {
    return {
      upcomingEventList: [],
      pastEventList: [],
      showNewEventForm: false,
      showRegisterForm: false,
      showSuccessfulReg: false
    }
  },
  created() {
    let outer;
    outer = this;
    axios.get("https://sheetdb.io/api/v1/mtwm963uzgiay").then(response => {
      response.data.forEach(function (item) {
        if(item.Upcoming === "T") {
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
      this.showSuccessfulReg = true;
    },
    openRegForm() {
      this.showRegisterForm = true;
    },
    closeSuccessReg() {
      this.showSuccessfulReg = false;
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
</style>
