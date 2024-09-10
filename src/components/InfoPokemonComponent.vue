<template>
   <section class="info-pokemon">
    <div class="container">
      <div class="img-pokemon">
        {{ pokemon.name }}
        <img :src="pokemon.sprites.front_default" alt="">
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    props:{
      pokemon: Object
    }
  }
</script>

<style lang="scss" scoped>

</style>