<template>
  <section class="p-3">
    <div class="bg-light p-3">
      <ul>
        <li v-for="(pokemon, i) in myPokemon" class="row"> 
          <div class="col-10 name" @click="showPokemon(pokemon)">
            {{ pokemon.charAt(0).toUpperCase() + pokemon.slice(1) }}
          </div>
          <div class="col-2 btn" @click="deletePokemon(i)"><font-awesome-icon :icon="['fas', 'trash']" /></div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
  export default {
    data(){
      return{
        myPokemon: [],
      }
    },
    props:{
      newPokemon: ''
    },
    methods:{
      getPokemon(){
        this.myPokemon = []

        for(let i = 0; i < localStorage.length; i++){
          
          const chiave = localStorage.key(i);
          this.myPokemon.push(JSON.parse(localStorage.getItem(chiave)))
        }
      },
      deletePokemon(i){
        localStorage.removeItem(localStorage.key(i));

        this.getPokemon()
      },
      updatePokemon(pokemon) {
        console.log('update' , pokemon)
        
        this.getPokemon()
      },
      showPokemon(pokemon){
        this.$emit('showPokemon', pokemon)
      }
    },
    mounted(){
      this.getPokemon()
    },
    watch:{
      newPokemon(newValue, oldValue){
        this.getPokemon()

      }
    }
  }
</script>

<style lang="scss" scoped>
@use '../scss/partials/my-pokemon.scss';
</style>