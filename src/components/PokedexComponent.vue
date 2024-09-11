<template>
  <main class="pokedex">
    <div class="container">
      <div class="row">
        <div class="col-6 border border-primary">
          <SearchComponent @newPokemon="refreshPokemon"/>
        </div>
        <div class="col-6 border border-primary">
          <MyPokemonComponent ref="myPokemonComponent" :newPokemon="newPokemon"/>
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

      }
    }
  }
</script>

<style lang="scss" scoped>

</style>