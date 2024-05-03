<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

    const route = useRoute();
    const { data: pokemon } = await useFetch('https://pokeapi.co/api/v2/pokemon/')
    const name = computed(() => route.params.name)

</script>

<template>
    <h1>{{ name }}</h1>
</template>
