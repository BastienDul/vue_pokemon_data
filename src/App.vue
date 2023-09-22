<script setup>
import Recherche from './components/Recherche.vue';
import Header from './components/Header.vue';
import Footer from './components/footer.vue';
import { onBeforeMount, ref } from 'vue';
const apiUrl = "https://pokebuildapi.fr/api/v1/pokemon/";
const allPokemon = ref([]);
onBeforeMount(() => {
  fetch(apiUrl)
    .then((response) => response.json())
    .then(data => {
      allPokemon.value = data;
      console.log(allPokemon.value);

    })

})
</script>

<template>
  <Header />

  <main>
    <Recherche :pokemonList = "allPokemon" />


  </main>


  <Footer />
</template>

<style >
@import "./assets/styles.css";
@import url(https://fonts.googleapis.com/css2?family=Bangers&display=swap);
</style>
