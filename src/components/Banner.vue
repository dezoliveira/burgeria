<template>
<div id="banner">
  <div class="info text-center py-4">
    <a>Faça o seu hamburger</a>
  </div>
</div>
</template>
<script>
export default {
  name: "Banner"
}
</script>
<style scoped>
  .info{
    color: white;
    font-size: 40px;
    margin: 50px;
    padding: 15px;
  }
  #banner{
    background-image: url('/img/Banner3.jpg');
    background-position: 280px -100px;
    background-size: cover;
    height: 700px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }
  .info{
    border-color: gold;
    border: 2px solid gold;
    font-size: 30px;
    transition: 0.5s all ease;
    text-transform: uppercase;
    font-weight:400;
  }

  .info:hover{
    transform: translateY(-40px);
  }
</style>