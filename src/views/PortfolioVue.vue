<script setup>
// fetch.js
import { ref } from 'vue'


const portfolio = ref(null)

fetch('http://127.0.0.1:8000/api/picture?page=1&limit=10').then((res) => res.json()).then((json) => {
  portfolio.value = json
  console.log(json);
})

</script>


<template>
  <div class="container-fluid portfolio">
    <div class="row">
      <div class="col-12">
        <h1>Portofolio</h1>
      </div>
    </div>

    <div class="row">
      <div v-for="pic in portfolio" class="col-12 col-md-4">
        <div class="card" style="width: 18rem;">
          <img v-bind:src="pic.url" class="card-img-top">
          <div class="card-body">
            <h5 class="card-title">{{ pic.title }} </h5>
            <p class="card-text"> {{ pic.description }} </p>
            <a v-bind:href=pic.url class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .portfolio {
    min-height: 100vh;
    display: flex;
    align-items: center;
    color: black;
    display: flex;
    flex-direction: row;

  }
}
</style>


  <div class="portfolio">
            
          </div>