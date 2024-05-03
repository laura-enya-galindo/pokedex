<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

    const { data: pokemonData } = await useFetch('https://pokeapi.co/api/v2/pokemon/')
    const pokemonList = pokemonData.value.results.slice(0, 10);
    const router = useRouter();

    const goToPokemon = (pokemonName: string) => {
        router.push(`/single/${pokemonName}`);
    };

</script>

<template>
    <div>
        <ul>
            <li v-for="(pokemon, i) in pokemonList" :key="i" class="pokemon-item" @click="goToPokemon(pokemon.name)">
                <div class="pokemon-card">
                    <p>{{ pokemon.name }}</p>
                    <button>More information</button>
                </div>
            </li>
        </ul>
    </div>
</template>

<style>
.pokemon-item {
  list-style: none;
  margin-bottom: 10px;
}

.pokemon-card {
  width: 200px;
  height: 100px;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.pokemon-card button {
  padding: 5px 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.pokemon-card button:hover {
  background-color: #0056b3;
}
</style>