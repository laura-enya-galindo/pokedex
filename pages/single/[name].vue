<script setup lang="ts">
import { ref } from 'vue';
import { useRoute } from 'vue-router';

    const route = useRoute();
    const { data: pokemon } = useFetch(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
    console.log(pokemon);
</script>

<template>
    <div>
        <div v-if="pokemon">
            <h1>{{ pokemon.name }}</h1>
            <p>Type: {{ pokemon.types.map(type => type.type.name).join(', ') }}</p>
            <img :src="pokemon.sprites.front_default" alt="Pokemon Image">
            <h2 v-if="pokemon.abilities.length">Abilities</h2>
            <ul>
                <li v-for="ability in pokemon.abilities" :key="ability.ability.name">{{ ability.ability.name }}</li>
            </ul>
            <div v-if="pokemon.stats.length">
                <h2>Stats</h2>
                <ul>
                    <li v-for="stat in pokemon.stats" :key="stat.stat.name">{{ stat.stat.name }}: {{ stat.base_stat }}</li>
                </ul>
            </div>
        </div>

        <div v-else>
            <p>This Pokemon does not exist.</p>
        </div>
    </div>
</template>
