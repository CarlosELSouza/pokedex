<template>
    <div v-if="pokemon" class="transition-all flex items-center justify-center flex-col w-80 bg-yellow-300 border-4 border-blue-500">
        <h2 class="text-3xl font-bold pb-5">{{ pokemon.name }}</h2>
        <img class="border-2 border-yellow-500 p-4 mb-6" :src="pokemon.sprites.front_default" alt="pokemon image">
        <p class="font-thin">Height: <span class="font-semibold">{{ pokemon.height }}</span></p>
        <p class="font-thin">Weight: <span class="font-semibold">{{ pokemon.weight }}</span></p>
        <p class="font-thin">Base Experience: <span class="font-semibold">{{ pokemon.base_experience }}</span></p>
    </div>
</template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'PokemonDetails',
    props: {
      pokemonUrl: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        pokemon: null
      };
    },
    watch: {
      pokemonUrl: 'fetchPokemonDetails'
    },
    created() {
      this.fetchPokemonDetails();
    },
    methods: {
      async fetchPokemonDetails() {
        if (!this.pokemonUrl) return;
        try {
          const response = await axios.get(this.pokemonUrl);
          this.pokemon = response.data;
        } catch (error) {
          console.error("Erro ao buscar detalhes do Pokémon:", error);
        }
      }
    }
  };
  </script>