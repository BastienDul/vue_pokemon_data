<script setup>
const apiUrl = "https://pokebuildapi.fr/api/v1/pokemon/";
import DetailPokemon from './DetailPokemon.vue';
import {ref} from 'vue';
const props = defineProps({
  pokemonList: Array
})
const pokemonSelected = ref("");
const pokemonData = ref({})
const isPokemon = ref(false);
function chercherPokemon() {
  console.log("Bouton cliqué");
  fetch(apiUrl + pokemonSelected.value)
  .then(res => res.json())
  .then(pokemon =>{
    console.log("pokémon recup : ", pokemon)
    pokemonData.value = pokemon;
    isPokemon.value = true;
  })
}

</script>

<template>
    <article>
      <h1>Information Pokémon</h1>

      <form action="" id="">
        <select name="pokemon" id="selectPokemon" v-model="pokemonSelected">
          <option v-for="OnePokemon in pokemonList" :value="OnePokemon.id">{{OnePokemon.id + " | " + OnePokemon.name }}</option>
        </select>

        <button @click.prevent="chercherPokemon" type="submit">Cliquez ici</button>
        <DetailPokemon v-if="isPokemon === true" :pokemonDetail="pokemonData"/>
      </form>
    </article>
</template>
