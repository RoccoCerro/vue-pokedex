<template>
  <main class="pokedex">
    <div class="container">
      <div class="row">
        <div class="col-6 border border-primary">
          <SearchComponent />
        </div>
        <div class="col-6 border border-primary">

        </div>
      </div>
    </div>
  </main>
</template>

<script>
import SearchComponent from './SearchComponent.vue'

  export default {
    components:{
      SearchComponent
    }    
  }
</script>

<style lang="scss" scoped>

</style>