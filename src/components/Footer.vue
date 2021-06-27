<template>
  <div class="footer"><h3>Copyright &copy; {{new Date().getFullYear()}} <a href="https://www.linkedin.com/in/theanmolsharma/">Anmol Sharma</a></h3></div>
</template>

<script>
export default {
  name: "Footer",
}
</script>

<style scoped>
.footer {
  width: 100vw;

  display: flex;
  justify-content: center;
  align-items: center;
}
.footer h3 {
  text-align: center;
  font-size: 20px;
  font-weight: lighter;
  margin-bottom: 30px;
}
.footer h3 a {
  color: white;
  text-decoration: none;
}
</style>