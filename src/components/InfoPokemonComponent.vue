<template>
   <section class="info-pokemon">
    <div class="container">
      <div v-if="pokemon">
        <div v-if="pokemon.sprites" class="img-pokemon">
          <img :src="pokemon.sprites.front_default" alt="">
        </div>
        <div v-if="pokemon.abilities" class="abilities">
          <h6>Abilities: </h6>
          <ul>
            <li v-for="ability in pokemon.abilities">
              {{ ability.ability.name }}
            </li>
          </ul>
        </div>
        <div class="stats">
          <h6>Stats:</h6>
          <ul>
            <li v-for="stats in pokemon.stats" class="row">
              <div class="stat col">
                {{ stats.stat.name }}
              </div>
              <div class="progress-stat col">
                <progress id="file" max="100" :value="stats.base_stat"></progress>
              </div>
            </li>
          </ul>
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