<script setup lang="ts">
import { useRouter } from 'vue-router';

const router = useRouter();

let searchPokemon = ref("");

const goToPokemon = () => {
    router.push(`/single/${searchPokemon.value}`);
};


</script>

<template>
    <input type="search" name="pokemon-search" id="pokemon-search" v-model="searchPokemon" v-on:keyup.enter="goToPokemon">
</template>