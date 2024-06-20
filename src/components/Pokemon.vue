<template>
    <li @click="selectPokemon" class="hover:bg-yellow-300 transition-all hover:border-blue-600 hover:border-2 cursor-pointer p-2 border-2 border-yellow-200">{{ pokemon.name }}</li>
</template>

<script>
export default {
  name: 'Pokemon',
  props: {
    pokemon: {
      type: Object,
      required: true
    }
  },
  methods: {
    selectPokemon() {
        console.log("foi")
        this.$emit('pokemon-selected', this.pokemon.url);
    }
  }
};
</script>
