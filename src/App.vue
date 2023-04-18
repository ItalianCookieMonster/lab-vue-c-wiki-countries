<template>
  <div class="app">
    <NavBar/>
    <router-view/>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    NavBar,
  },

  // data(){
  //   return {
  //     countries: []
  //   }
  // },

  // methods: {
  //   _getCountriesData(){
  //     fetch('https://ih-countries-api.herokuapp.com/countries')
  //           .then(response => response.json())
  //           .then(data => {
  //               this.countries = data.map(elem => ({
  //                   alpha2Code: elem.alpha2Code.toLowerCase(),
  //                   alpha3Code: elem.alpha3Code,
  //                   name: elem.name.common,
  //                   borders: elem.borders,
  //                   capital: elem.capital[0],
  //                   area: elem.area
  //               }))
  //           })
  //   }


  // },

  // created(){
  //   this._getCountriesData()
  // }
}

</script>

<style>

</style>