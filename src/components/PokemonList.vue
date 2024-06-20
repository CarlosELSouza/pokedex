<template>
    <div class="flex justify-center w-full gap-4">
        <div class="flex items-center flex-col justify-center">
            <h2 class="p-4 text-yellow-500">Click to see details:</h2>
            <ul class="w-96 flex flex-col gap-2 h-[500px] overflow-auto">
                <Pokemon v-for="pokemon in pokemons" :key="pokemon.name" :pokemon="pokemon"  @pokemon-selected="showPokemonDetails" />
            </ul>
        </div>
        <div class="flex items-center justify-center">
            <PokemonDetails v-if="selectedPokemonUrl" :pokemonUrl="selectedPokemonUrl" />
        </div>
    </div>
</template>
  
<script>
import axios from 'axios';
import Pokemon from './Pokemon.vue';
import PokemonDetails from './PokemonDetails.vue';

export default {
    name: 'PokemonList',
    components: {
        Pokemon,
        PokemonDetails
    },
    data() {
        return {
            pokemons: [],
            selectedPokemonUrl: null
        };
    },
    created() {
        this.fetchPokemons();
    },
    methods: {
        async fetchPokemons() {
            try {
                console.log("fetching...")
                const response = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=151');
                this.pokemons = response.data.results;
            } catch (error) {
                console.error("Erro ao buscar Pokémon:", error);
            }
        },
        showPokemonDetails(url) {
            this.selectedPokemonUrl = url;
        }
    },
};
</script>