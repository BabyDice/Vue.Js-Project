<script setup>
// fetch.js
import { ref } from 'vue'


const portfolio = ref(null)



let displayPage = ref(page)
let page = 1;
const moovingPage = (way = '') => {
  switch (way) {
    case 'next':
      page++;
      break

    case 'prev':
      page > 1 ? page-- : null;
      break

      break;

    default:
      break;
  }
  displayPage.value = page
}

const loadPic = (page = 1) => {

  fetch('http://127.0.0.1:8000/api/picture?page=' + page + '&limit=6').then((res) => res.json()).then((json) => {
    portfolio.value = json
    console.log(json);
  })
}

(loadPic)()

</script>


<template>

  <nav aria-label="...">
    <ul class="pagination d-flex justify-content-center m-t-2">
      <li v-bind:class="{ 'page-item': true, 'disabled': displayPage===1}">
        <span class="page-link" @click="moovingPage('prev')">Previous</span>
      </li>
      <li class="page-item"><a class="page-link" href="#">1</a></li>
      <li class="page-item active" aria-current="page">
        <span class="page-link">2</span>
      </li>
      <li class="page-item"><a class="page-link" href="#">3</a></li>
      <li class="page-item">
        <a class="page-link" href="#" @click="moovingPage('next')">Next</a>
      </li>
    </ul>
  </nav>

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

  <nav aria-label="...">
    <ul class="pagination d-flex justify-content-center m-t-4">
      <li v-bind:class="{ 'page-item': true, 'disabled': displayPage===1}">
        <span class="page-link" @click="moovingPage('prev')">Previous</span>
      </li>
      <li class="page-item"><a class="page-link" href="#">1</a></li>
      <li class="page-item active" aria-current="page">
        <span class="page-link">2</span>
      </li>
      <li class="page-item"><a class="page-link" href="#">3</a></li>
      <li class="page-item">
        <a class="page-link"  @click="moovingPage('next')">Next</a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.portfolio {
  color: black;
}
</style>
