<template>
  <section class="search-pokemon">
    <div class="container">
      <!-- <form action=""> -->
        <div class="row">
          <div class="col-8">
            <input v-model="name" class="form-control" type="text" placeholder="Pokemon">
          </div>
          <div class="col-4">
            <button @click="fetchPokemon" class="btn btn-dark">Search</button>
          </div>
        </div>
      <!-- </form> -->
    </div>
  </section>
  <InfoPokemonComponent :pokemon="pokemon"/>
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
        pokemon: {}
      }
    },
    methods:{
      fetchPokemon(){
        axios.get('https://pokeapi.co/api/v2/pokemon/' + this.name)
        .then(res => {
          console.log(res.data)
          this.pokemon = res.data
        })
        .catch(error => {
          if (error.response && error.response.status === 404) {
            console.error('Il nome inserito non è un pokemon!'); // Messaggio personalizzato per 404
          } else {
            console.error('Errore nella richiesta API:', error); // Gestisci altri errori
          }
        });
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>