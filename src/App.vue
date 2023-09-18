<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const moviesGenres = ref([])
const TVGenres = ref([])

onMounted(async () => {
  let response = await axios.get('https://api.themoviedb.org/3/genre/movie/list?language=pt-BR', {
    headers: {
      Authorization: `Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI4YzMwZDBlZTc5MDI0NTczZmQxOWUyYTgxZGFlZDgzMSIsInN1YiI6IjY0ZmYxYmZkZWZlYTdhMDBlMDM0YjE3OSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.vXVSnex1oSdSFntUiN0yggkBCpGDbFupNrq_VKAsV74`
    }
  })
  moviesGenres.value = response.data.genres
  response =  await axios.get('https://api.themoviedb.org/3/genre/tv/list?language=pt-BR', {
    headers: {
      Authorization: `Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI4YzMwZDBlZTc5MDI0NTczZmQxOWUyYTgxZGFlZDgzMSIsInN1YiI6IjY0ZmYxYmZkZWZlYTdhMDBlMDM0YjE3OSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.vXVSnex1oSdSFntUiN0yggkBCpGDbFupNrq_VKAsV74 `
    }
  })
  TVGenres.value = response.data.genres
})
</script>

<template>
  <h1>Gêneros de filmes</h1>
  <ul>
    <li v-for="genre in moviesGenres" :key="genre.id">
      {{ genre.id }} - 
      {{ genre.name }}
   
    </li>
  </ul>
  <hr />
  <h1>Gêneros de programas de TV</h1>
  <ul>
    <li v-for="genre in TVGenres" :key="genre.id">
      {{ genre.id }} - 
      {{ genre.name }}

    </li>
  </ul>
</template>