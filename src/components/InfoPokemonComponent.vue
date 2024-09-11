<template>
   <section class="info-pokemon">
    <div class="container">
      <div v-if="pokemon">
        <div v-if="pokemon.sprites" class="img-pokemon">
          <div>
            <div class="slideshow"> 
              <img :src="pokemon.sprites.front_default" alt="">
              <img :src="pokemon.sprites.back_shiny" alt="">
            </div>
          </div>
        </div>
        <div class="info" v-if="pokemon.name">
          <ul class="list-unstyled">
            <li><strong>Name:</strong> {{ pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1) }}</li>
            <li><strong>Height:</strong> {{ pokemon.height }}</li>
            <li><strong>Weight:</strong> {{ pokemon.weight }}</li>
          </ul>
          <!-- <div v-if="pokemon.abilities" class="abilities">
            <h6>Abilities: </h6>
            <ul>
              <li v-for="ability in pokemon.abilities">
                {{ ability.ability.name.charAt(0).toUpperCase() + ability.ability.name.slice(1) }}
              </li>
            </ul>
          </div> -->
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
@use '../scss/partials/info-pokemon.scss';
</style>