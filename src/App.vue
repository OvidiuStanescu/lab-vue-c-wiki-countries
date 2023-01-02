<template>
  <div>
    <NavbarComponent></NavbarComponent>
    <div class="container">
      <div class="row">
        <CountriesListComponent v-if="data" :data = "data"></CountriesListComponent>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarComponent from"./components/NavbarComponent.vue"
import CountriesListComponent from "./components/CountriesListComponent.vue"
export default{
  components:{
    NavbarComponent,
    CountriesListComponent
  },

  data() {
    return {
      data: []
    }
  },

  async created() {
    const response = await fetch('https://ih-countries-api.herokuapp.com/countries');
    this.data = await response.json();
  }
}

</script>

<style>

</style>