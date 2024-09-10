<template>
  <section class="search-pokemon">
    <div class="container">
      <!-- <form action=""> -->
        <div class="row">
          <div class="col-8 my-col">
            <input v-model="name" class="form-control my-input" type="text" placeholder="Pokemon">
          </div>
          <div class="col-4 my-col">
            <button @click="fetchPokemon" class="btn btn-dark my-btn">Search</button>
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
            console.error('Il nome inserito non è un pokemon!');
             // Messaggio personalizzato per 404
            this.error = 'Il nome inserito non è un pokemon!'
          } else {
            console.error('Errore nella richiesta API:', error);
          }
        });
      }
    }
  }
</script>

<style lang="scss" scoped>
  // .my-col{
  //   min-width: 100px;
  // }
</style>