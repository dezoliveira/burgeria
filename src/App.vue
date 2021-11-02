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
import Banner from './components/Banner.vue'

export default {
  data(){
    return {
      logoBurgeria: "img/Logo.jpg",
      altBurgeria: "Burgeria"
    }
  },
  components: {
    Navbar,
    Footer,
    Banner
  },
}
</script>

<style>
  *{
    box-sizing: border-box;
  }
</style>
