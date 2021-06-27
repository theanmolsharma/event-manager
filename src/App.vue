<template>
  <div class="main-cont">
    <Header></Header>
    <NewList :upcomingEventList="upcomingEventList" @openRegForm="openRegForm"></NewList>
    <PastList :pastEventList="pastEventList"></PastList>
    <div class="spacer"></div>
    <div class="btn-container">
      <button type="button" class="btn btn-outline-light btn-lg" @click="openEventForm">Add new Event</button>
    </div>
    <div class="btn-container">
      <button type="button" class="btn btn-outline-light btn-lg" @click="showData">Show Registered</button>
    </div>
    <div class="spacer"></div>
    <RegisterForm v-if="showRegisterForm" :eventName="eventName" @closeRegForm="closeRegForm"></RegisterForm>
    <SuccessfulReg v-if="showSuccessfulReg" @closeSuccessReg="closeSuccessReg"></SuccessfulReg>
    <NewEventForm v-if="showNewEventForm" @closeEventForm="closeEventForm" @updateList="updateList"></NewEventForm>
    <ShowRegistered v-if="showRegistered" @closeShowRegistered="closeData" @showData="showTable"></ShowRegistered>
    <DataTable v-if="showDataTable" @closeDataTable="closeDataTable" :registeredData = "registeredData"></DataTable>
    <Footer></Footer>
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
import ShowRegistered from "./components/ShowRegistered";
import DataTable from "./components/DataTable";
import Footer from "./components/Footer";

export default {
  name: 'App',
  components: {Footer, DataTable, ShowRegistered, NewEventForm, SuccessfulReg, RegisterForm, PastList, NewList, Header},
  data() {
    return {
      upcomingEventList: [],
      pastEventList: [],
      showNewEventForm: false,
      showRegisterForm: false,
      showSuccessfulReg: false,
      showRegistered: false,
      showDataTable: false,
      eventName: "",
      registeredData: []
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
    openRegForm(name) {
      console.log(name)
      this.eventName = name;
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
    showData() {
      this.showRegistered = true;
    },
    closeData() {
      this.showRegistered = false;
    },
    closeDataTable() {
      this.showDataTable = false;
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
    },
    showTable(data) {
      this.closeData();
      this.showDataTable = true;
      data.sort((a,b) => (a.event > b.event) ? 1 : ((b.event > a.event) ? -1 : 0))
      this.registeredData = data;
    },
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
  background-image: linear-gradient(66.47deg, #120d4f, #5e12ce);
}
.btn-container button {
  border-radius: 25px;
  padding: 10px 40px 10px;
}
.spacer {
  height: 10vh;
  width: 100vw;
}
</style>
