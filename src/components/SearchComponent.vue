<template>
  <section class="search-pokemon">
    <div class="container">
      <!-- <form action=""> -->
        <div class="row">
          <div class="col-6 my-col">
            <input v-model="name" class="form-control my-input" type="text" placeholder="Pokemon">
          </div>
          <div class="col-3 my-col">
            <button @click="fetchPokemon" class="btn btn-dark my-btn">Search</button>
          </div>
          <div class="col-3">
            <button @click="capturePokemon" class="btn btn-outline-dark my-btn">Capture</button>
          </div>
        </div>
      <!-- </form> -->
    </div>
  </section>
  <InfoPokemonComponent :pokemon="pokemon" :error="error"/>
</template>

<script>
  import InfoPokemonComponent from './InfoPokemonComponent.vue'
  import axios from 'axios'

  export default {
    components:{
      InfoPokemonComponent
    },
    data(){
      return{
        name: '',
        pokemon: {},
        error: ''
      }
    },
    methods:{
      fetchPokemon(){
        this.pokemon = {}
        this.error = ''

        axios.get('https://pokeapi.co/api/v2/pokemon/' + this.name)
        .then(res => {
          console.log(res.data)
          this.pokemon = res.data
        })
        .catch(error => {
          if (error.response && error.response.status === 404) {
            console.error('The name you entered is not a Pokemon!');
             // Messaggio personalizzato per 404
            this.error = 'The name you entered is not a Pokemon!'
          } else {
            console.error('Error in API request:', error);
          }
        });
      },
      capturePokemon(){

        if(this.pokemon.id === undefined){
          alert('Search for a pokemon!')
        }else{
          localStorage.setItem(this.pokemon.id, JSON.stringify(this.pokemon.name))
          this.$emit('newPokemon', this.pokemon)

        }
      },
      emits: ['newPokemon'],
      forceFetchPokemon(name){
        this.name = name

        this.fetchPokemon()
      }
    }
  }
</script>

<style lang="scss" scoped>
  // .my-col{
  //   min-width: 100px;
  // }
</style>