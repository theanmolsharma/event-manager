<template>
<div>
  <div><h1 class="event-heading mt-5">Upcoming Events</h1></div>
  <div>
    <div class="container mt-3">
      <div class="row justify-content-center">
        <NewListItem v-for="event in upcomingEventList" :event="event" :key="event.Name" @openRegForm="openRegForm"></NewListItem>
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
  props: ['upcomingEventList'],
  methods: {
    openRegForm() {
      this.$emit('openRegForm');
    }
  }
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