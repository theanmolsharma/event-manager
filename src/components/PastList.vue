<template>
  <div>
    <div><h1>Past Events</h1></div>
    <div>
      <div class="container mt-5">
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

</style>