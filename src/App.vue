<script setup>
  import PokemonList from './components/PokemonList.vue';
</script>

<template>
  <main class="bg-yellow-100 h-[100vh] w-full flex flex-col items-center">
    <div class="p-4">
      <h1 class="font-thin text-2xl text-yellow-500">online <span class="font-extrabold">pokedéx</span></h1>
    </div>

    <div class="w-80 flex justify-between p-2 mb-4 bg-yellow-100"><p>Generation:</p><p>1</p></div>

    <div class="w-full h-full p-2">
      <PokemonList/>
    </div>
  </main>
</template>

<style scoped>

</style>
