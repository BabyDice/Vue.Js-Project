<!-- IMPORTATION -->

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue';
</script>

<!-- END IMPORTATION -->

<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->
    <Navbar />

    <!-- <div class="wrapper">
      <HelloWorld msg="Catch  ! " />
      <HelloWorld msg="Back  ! " />
      <HelloWorld msg="Go  ! " />
      
    </div> -->
  </header>
  <RouterView />
  <Footer/>
</template>

<!-- CSS / STYLE  -->

<style>
@import '@/assets/base.css';


@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}
</style>

<!-- END CSS / STYLE  -->