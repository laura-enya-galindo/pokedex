<script setup lang="ts">
import { ref, reactive } from 'vue';

    let search: string = "";
    const pokemonList = reactive<string[]>([]);

    function searchPokemon() {
        if (search.trim() !== "") {
            // Recherche d'un pokémon
        }
        search = "";
    }

    function goToInformation(index: number) {

    }
</script>

<template>
    <div>
        <input type="text" v-model="search">
        <button @click="searchPokemon">Search Pokemon</button>

        <ul>
            <li v-for="(pokemon, i) in pokemonList">{{ pokemon }} <button @click="goToInformation(i)"> More information </button></li>
        </ul>

        <!--Créer condition pour afficher le résultat de la recherche-->
        <p v-if="pokemonList.length >= 10">Tu as 10 tâches à faire !</p>

    </div>
</template>