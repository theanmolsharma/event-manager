<template>
<div>
  <div><h1>Upcoming Events</h1></div>
  <div>
    <div class="container mt-5">
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
</style>