<script setup lang="ts">
import { useQuery } from '@tanstack/vue-query'

const pokemonsQuery = useQuery({
  queryKey: ['pokemons'],
  queryFn: ({ signal }) => fetch('https://pokeapi.co/api/v2/pokemon/ditto', { signal })
    .then(response => response.json()),
})
</script>

<template>
  <div v-if="pokemonsQuery.isLoading.value">
    Loading...
  </div>
  <div v-else>
    {{ pokemonsQuery.data }}
  </div>
</template>
