<template>
  <section>
    <div>
      <ul>
        <li v-for="(pokemon, i) in myPokemon" @click="deletePokemon(i)"> {{ pokemon }}</li>
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

</style>