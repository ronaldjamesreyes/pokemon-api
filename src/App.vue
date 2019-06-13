<template>
  <div id="app">
    <div class="container">
      <h1 class="text-center display-1 m-5">Rock Type Pokemon</h1>
      <div class="row">
        <Card :url="item.pokemon.url" v-for="item in pokemon_rocktype" :key="item.pokemon.name"></Card>
      </div>
    </div>
  </div>
</template>

<script>

import Card from './components/Card.vue'

export default {
  name: 'app',
  components: {
    Card
  },
  data: function () {
    return {
      pokemon_rocktype:""
    }
  },
  mounted: function() {
    console.log("mounted function ran")
    const axios = require('axios');
    const vm = this;
    axios({
        method: 'get',
        url: 'https://pokeapi.co/api/v2/type/rock',
        responseType: 'stream'
    })
    .then(function (response) {
        vm.pokemon_rocktype = response.data.pokemon
    });
  }
}

</script>

<style>

</style>
