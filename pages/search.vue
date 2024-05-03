<script setup lang="ts">
    definePageMeta({
        layout: 'custom'
    });

    const router = useRouter();

    let searchPokemon = ref("");

    const goToPokemon = () => {
        router.push(`/single/${searchPokemon.value}`);
    };
</script>

<template>
    <input type="search" name="pokemon-search" id="pokemon-search" v-model="searchPokemon" v-on:keyup.enter="goToPokemon" placeholder="Search your pokemon">
</template>


<style>
    input {
        height: 2.5rem;
        padding-left: 0.625rem;
        margin-left: 0.675rem;
        border-radius: 2px;
        border: 1px solid #484848;
    }
</style>