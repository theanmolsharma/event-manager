<template>
  <div>
    <div><h1>Upcoming Events</h1></div>
    <div>
      <div class="container mt-5">
        <div class="row justify-content-center">
          <PastListItem></PastListItem>
          <PastListItem></PastListItem>
          <PastListItem></PastListItem>
          <PastListItem></PastListItem>
          <PastListItem></PastListItem>
          <PastListItem></PastListItem>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PastListItem from "./PastListItem";
export default {
  name: "PastList",
  components: {PastListItem},
  props: ['pastEventList'],
}
</script>

<style scoped>

</style>