<template>
<div>
  <Navbar :logo="logoBurgeria" :alt="altBurgeria" />
    <div class="col-lg-12 col-md-12 col-sm-12">
      <router-view />
      <Footer />
    </div>
</div>
</template>
<script>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

export default {
  data(){
    return {
      logoBurgeria: "img/Logo5.png",
      altBurgeria: "Burgeria"
    }
  },
  components: {
    Navbar,
    Footer,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,500;0,700;1,200;1,600&family=Potta+One&display=swap');
  *{
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
  }
</style>
