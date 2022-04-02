<template>
  <div class="PokemonComponent">
    <PokemonComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import PokemonComponent from '@/components/PokemonComponent.vue'

export default {
  name: 'PokeApp',
  components: {
    PokemonComponent
  }
}
</script>
