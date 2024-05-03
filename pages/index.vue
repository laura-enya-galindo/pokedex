<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

    const { data: pokemonData } = await useFetch('https://pokeapi.co/api/v2/pokemon/')
    const pokemonList = pokemonData.value.results.slice(0, 10);
    
    const router = useRouter();

    let searchPokemon = ref("");

    const goToPokemonFromList = (pokemonName: string) => {
        router.push(`/single/${pokemonName}`);
    };

    const goToPokemonFromSearch = () => {
      router.push(`/single/${searchPokemon.value}`);
    };

</script>

<template>
    <div>
      <input class="home-search" type="search" name="pokemon-search" id="pokemon-search" v-model="searchPokemon" v-on:keyup.enter="goToPokemonFromSearch" placeholder="Search for a Pokemon">
      <div class="container-pokemons">
          <div v-for="(pokemon, i) in pokemonList" :key="i" class="pokemon-item" @click="goToPokemonFromList(pokemon.name)">
              <div class="pokemon-card">
                  <p>{{ pokemon.name }}</p>
                  <button>More information</button>
              </div>
            </div>
        </div>
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
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .pokemon-card p {
    margin-top: 0;
  }

  .pokemon-card button {
    padding: 5px 10px;
    background-color: #484848;
    color: white;
    border: none;
    border-radius: 2px;
    transition: all 1s ease-in-out;
    cursor: pointer;
  }

  .pokemon-card button:hover {
    background-color: black;
  }

  .home-search {
    margin-left: 0;
    margin-top: 0.625rem;
  }

  .container-pokemons {
    display: grid;
    grid-template-columns: repeat(5,1fr);
    grid-gap: 0.625rem;
    margin-top: 1.25rem;
  }

  @media screen and (max-width:1000px) {
    .container-pokemons {
      grid-template-columns: repeat(4,1fr);
    }
  }

  @media screen and (max-width:900px) {
    .container-pokemons {
      grid-template-columns: repeat(3,1fr);
    }
  }

  @media screen and (max-width:700px) {
    .container-pokemons {
      grid-template-columns: repeat(2,1fr);
    }
  }

  @media screen and (max-width:500px) {
    .container-pokemons {
      grid-template-columns: 1fr;
    }
  }
</style>