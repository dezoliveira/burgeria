<template>
  <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-dark p-0 px-5 d-flex justify-content-between">
    <div class="navbrand">
      <router-link to="/">
        <a class="navbar-brand text-white" href="#">
          <img :src="logo" :alt="alt" id="logo">
        </a>
       </router-link>
    </div>
    <div class="nav-itens text-warning">
      <router-link to="/">Home</router-link>
      <router-link to="/pedidos">Pedidos</router-link>
    </div>
  </nav>
</template>
<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"]
}
</script>
<style scoped>
  img{
    width: 50px;
  }

  .nav-itens a{
    color: gold;
    text-decoration: none;
    list-style: none;
    margin-left: 20px;
    font-size: 18px;
    font-weight: 600;
  }
  .nav-itens a:hover{
    color: #fff;
  }
</style>