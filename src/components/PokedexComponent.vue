<template>
  <main class="pokedex">
    <div class="container">
      <div class="row">
        <div class="col-6 border border-primary">
          <SearchComponent />
          <InfoPokemonComponent />
        </div>
        <div class="col-6 border border-primary">

        </div>
      </div>
    </div>
  </main>
</template>

<script>
import SearchComponent from './SearchComponent.vue'
import InfoPokemonComponent from './InfoPokemonComponent.vue'

  export default {
    components:{
      SearchComponent,
      InfoPokemonComponent
    }    
  }
</script>

<style lang="scss" scoped>

</style>