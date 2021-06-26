<template>
  <div>
    <Header></Header>
    <NewList :upcomingEventList="upcomingEventList"></NewList>
    <PastList :pastEventList="pastEventList"></PastList>
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/Header";
import NewList from "./components/NewList";
import PastList from "./components/PastList";
export default {
  name: 'App',
  components: {PastList, NewList, Header},
  data() {
    return {
      upcomingEventList: [],
      pastEventList: []
    }
  },
  created() {
    let outer;
    outer = this;
    axios.get("https://sheetdb.io/api/v1/mtwm963uzgiay").then(response => {
      response.data.forEach(function (item) {
        if(item.Upcoming == "T") {
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
}
</script>

<style>

</style>
