<template>
   <section class="info-pokemon">
    <div class="container">
      <div v-if="pokemon">
        <div v-if="pokemon.sprites" class="img-pokemon">
          <img :src="pokemon.sprites.front_default" alt="">
        </div>
      </div>
      <div>
        {{ error }}
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    props:{
      pokemon: Object,
      error: String
    }
  }
</script>

<style lang="scss" scoped>

</style>