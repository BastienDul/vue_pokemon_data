<script setup>
import { ref } from 'vue';
const props = defineProps({
    pokemonDetail: Object
})
const cache = ref(false);
</script>

<template>
    
    <section id="total_poke">
        <Transition>
            <div id="gauche_poke">
                    <h2>detail de {{ pokemonDetail.name }}</h2>
                    <img v-bind:src="pokemonDetail.image" alt="{{ pokemonDetail.detail }}">
                    <p>Élément : {{ pokemonDetail.apiTypes.map((nomType)=> nomType.name).join(", ")}}</p>
                    <p v-if="pokemonDetail.apiEvolutions[0] !== undefined">Évolution :  {{ pokemonDetail.apiEvolutions.map((nomEvolutions) => nomEvolutions.name).join(", ")}}</p>
            </div>
        </Transition>

        <Transition>
            <div v-if="cache" id="droite_poke">
                    <h2>Les statistiques :</h2>
                    <p>Points de vie : {{pokemonDetail.stats.HP}}</p>
                    <p>Attaque : {{pokemonDetail.stats.attack}}</p>
                    <p>Défense : {{pokemonDetail.stats.defense}}</p>
                    <p>Attaque spécial : {{pokemonDetail.stats.special_attack}}</p>
                    <p>Défense spécial : {{pokemonDetail.stats.special_defense}}</p>
                    <p>Vitesse : {{pokemonDetail.stats.speed}}</p> 
            </div>
        </Transition>

    </section>
    
    <button @click="cache = !cache" type="button">En savoir plus</button>




</template>