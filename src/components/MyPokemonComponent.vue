<template>
  <section>
    <ul>
      <li v-for="pokemon in myPokemon"> {{ pokemon }}</li>
    </ul>
  </section>
</template>

<script>
  export default {
    data(){
      return{
        myPokemon: [],
        chiave: null 
      }
    },
    props:{
      newPokemon: ''
    },
    methods:{
      getPokemon(){
        this.myPokemon = []

        for(let i = 0; i < localStorage.length; i++){
          
          this.chiave = localStorage.key(i);
          this.myPokemon.push(JSON.parse(localStorage.getItem(this.chiave)))
        }

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