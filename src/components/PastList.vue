<template>
  <div>
    <div><h1 class="event-heading mt-5">Past Events</h1></div>
    <div>
      <div class="container mt-3">
        <div class="row justify-content-center">
          <PastListItem v-for="event in pastEventList" :event="event" :key="event.Name"></PastListItem>
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
.event-heading {
  font-family: Raleway;
  font-style: normal;
  font-weight: 800;

  font-size: clamp(35px, 3.5vw, 105px);
  text-align: center;
  z-index: 5;

  color: #FFFFFF;
}
</style>