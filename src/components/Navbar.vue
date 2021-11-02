<template>
  <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-dark px-5 d-flex justify-content-between">
    <div class="navbrand">
      <router-link to="/">
        <a class="navbar-brand text-white" href="#">
          <img :src="logo" :alt="alt" id="logo">LA BURGERIA
        </a>
       </router-link>
    </div>
    <div class="nav-itens">
      <router-link to="/">Home</router-link> |
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
  *{
    text-decoration: none;
    font-size: 18px;
    font-weight: bold;
  }
  img{
    width: 32px;
  }
  .nav-itens a{
    color: gold;
    text-decoration: none;
    list-style: none;
  }

  router-link{
    color: blueviolet;
  }
</style>