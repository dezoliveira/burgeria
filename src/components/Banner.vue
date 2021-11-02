<template>
<div id="banner">
  <div class="info">
    <p>Faça o seu hamburger</p>
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
</style>