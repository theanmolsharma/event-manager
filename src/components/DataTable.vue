<template>
<div class="table-cont">
  <div class="cont-1">
    <div class="spacer" style="height: 6vh; width: 100%">
      <button type="button" class="btn btn-outline-danger btn-sm close btn-extra" @click="closeDataTable">Close</button>
    </div>
    <table class="table .table-bordered border-dark table-striped">
      <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Contact</th>
        <th scope="col">Email</th>
        <th scope="col">Event Registered</th>
      </tr>
      </thead>
      <tbody>
      <TableItem v-for="data in registeredData" :data="data" :key="data.email"></TableItem>
      </tbody>
    </table>
  </div>
</div>
</template>

<script>
import TableItem from "./TableItem";
export default {
  name: "DataTable",
  components: {TableItem},
  props: ['registeredData'],
  methods: {
    closeDataTable() {
      this.$emit("closeDataTable");
    }
  }
}
</script>

<style scoped>
.table-cont {
  position: fixed;
  background-image: linear-gradient(66.47deg, #120d4f, #5e12ce);
  top: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 6;
}
.cont-1 {
  background: white;
  width: 90vw;
  padding: 20px 30px 30px;
  border: 2px solid black;
  border-radius: 40px;
  z-index: 7;
}
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
</style>