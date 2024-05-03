<script setup lang="ts">
    definePageMeta({
        layout: 'custom-search'
    });

    const router = useRouter();

    let searchPokemon = ref("");

    const goToPokemon = () => {
        router.push(`/single/${searchPokemon.value}`);
    };
</script>

<template>
    <input type="search" name="pokemon-search" id="pokemon-search" v-model="searchPokemon" v-on:keyup.enter="goToPokemon">
</template>