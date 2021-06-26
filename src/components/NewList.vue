<template>
<div>
  <div><h1>Upcoming Events</h1></div>
  <div>
    <div class="container mt-5">
      <div class="row justify-content-center">
        <NewListItem></NewListItem>
        <NewListItem></NewListItem>
        <NewListItem></NewListItem>
        <NewListItem></NewListItem>
        <NewListItem></NewListItem>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import NewListItem from "./NewListItem";
export default {
  name: "NewList",
  components: {NewListItem},
  props: ['upcomingEventList']
}
</script>

<style scoped>
</style>