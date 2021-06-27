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

  background-image: url("../assets/5335415.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  display: flex;
  align-items: center;
  justify-content: center;
}
.inner {
  width: 70vw;
  margin-bottom: 10vh;
}
.inner h1, h3{
  font-family: Raleway;
  font-style: normal;
  font-weight: 800;

  font-size: clamp(50px, 5vw, 105px);

  z-index: 5;

  color: #FFFFFF;
}
.inner h3 {
  font-weight: 500;
  font-size: clamp(30px, 2.5vw, 85px);
}
</style>