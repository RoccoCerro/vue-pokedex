<template>
  <main class="pokedex">
    <div class="container">
      <div class="row vh-100">
        <div class="col-12 col-md-6 my-col-pokedex p-2">
          <SearchComponent ref="searchComponent" @newPokemon="refreshPokemon"/>
        </div>
        <div class="col-12 col-md-6 my-col-pokedex p-2">
          <MyPokemonComponent ref="myPokemonComponent" :newPokemon="newPokemon" @showPokemon="showPokemon"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import SearchComponent from './SearchComponent.vue'
import MyPokemonComponent from './MyPokemonComponent.vue';

  export default {
    data(){
      return{
        newPokemon: null
      }
    },
    components:{
      SearchComponent,
      MyPokemonComponent
    },
    methods:{
      refreshPokemon(pokemon){
        
        this.newPokemon = pokemon
        this.$refs.myPokemonComponent.updatePokemon(pokemon);

      },
      showPokemon(pokemon){
        this.$refs.searchComponent.forceFetchPokemon(pokemon);
      }
    }
  }
</script>

<style lang="scss" scoped>
@use '../scss/partials/pokedex.scss';
</style>