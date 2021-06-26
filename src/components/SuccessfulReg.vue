<template>
  <div class="cont">
    <div class="inner">
      <div class="spacer">
        <button type="button" class="btn btn-outline-danger btn-sm close" @click="closeSuccessReg">Close</button>
      </div>
      <div class="spacer"><h2>Hurray!! You have been registered successfully!!</h2></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SuccessfulReg",
  methods: {
    closeSuccessReg() {
      this.$emit('closeSuccessReg');
    }
  }
}
</script>

<style scoped>
.cont {
  position: fixed;
  top: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 6;
}
.spacer {
  width: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: flex-start;
}
.inner {
  width: max(50vw, 300px);
  background-color: white;
}
</style>