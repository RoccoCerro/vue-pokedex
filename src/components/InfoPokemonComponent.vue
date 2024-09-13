<template>
   <section class="info-pokemon">
    <div class="container">
      <div>
        <div class="img-pokemon">
          <div>
            <div v-if="pokemon.sprites" class="slideshow"> 
              <img :src="pokemon.sprites.front_default" alt="">
              <img :src="pokemon.sprites.back_shiny" alt="">
            </div>
            <div v-else class="w-100 h-100">
              <img class="img-pokeball w-100 h-100 object-fit-contain" src="/pokeball.webp" alt="">
            </div>
          </div>
        </div>
        <div class="info" :class="pokemon.name ?? 'height-content'">
          <ul class="list-unstyled" v-if="pokemon.name">
            <li><strong>Name:</strong> {{ pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1) }} </li>
            <li><strong>Height:</strong> {{ pokemon.height }} </li>
            <li><strong>Weight:</strong> {{ pokemon.weight }} </li>
          </ul>
          <div class="stats" v-if="pokemon.stats">
            <h6>Stats:</h6>
            <ul>
              <li v-for="stats in pokemon.stats" class="row">
                <div class="stat col">
                  {{ stats.stat.name.charAt(0).toUpperCase() + stats.stat.name.slice(1) }}
                </div>
                <div class="progress-stat col">
                  <progress id="file" max="100" :value="stats.base_stat"></progress>
                </div>
              </li>
            </ul>
          </div>
          <div>
            {{ error }}
          </div>
        </div>
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
@use '../scss/partials/info-pokemon.scss';
</style>