<template>
  <tr>
    <th scope="row">{{data.firstName}} {{data.lastName}}</th>
    <td>{{data.mobileNumber}}</td>
    <td>{{data.email}}</td>
    <td>{{data.event}}</td>
  </tr>
</template>

<script>
export default {
  name: "TableItem",
  props: ['data']
}
</script>

<style scoped>

</style>