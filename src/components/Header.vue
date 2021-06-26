<template>
<div class="header-container">
    <div class="inner">
      <h1>Organize Engaging Events, Faster!!</h1>
      <h3>This is a managing system – backed by open-source code – that helps you organize high-quality irresistible social experiences.</h3>
    </div>
</div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style>
.header-container {
  height: 100vh;
  width: 100vw;

  background-image: url("../assets/bg.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  display: flex;
  align-items: center;
  justify-content: center;
}
.inner {
  width: 60vw;
}
.inner h1, h3{
  text-align: center;
  color: aliceblue;
}
.inner h3 {
  font-size: 24px;
}
</style>