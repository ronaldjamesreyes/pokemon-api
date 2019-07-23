<template>
  <div id="app">
    <h5>created by Ronald Reyes</h5>
    <div class="container text-capitalize">
      <h1 class="text-center display-1 m-5">{{activeType}} Pokemon Type</h1>
      <span
        v-for="type in pokemon_types"
        class="btn btn-primary m-1"
        v-on:click="type_click(type.name)"
      >{{type.name}}</span>
      <div class="row">
        <Card :url="item.pokemon.url" v-for="item in pokemon_current" :key="item.pokemon.name"></Card>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";

export default {
  name: "app",
  components: {
    Card
  },
  data: function() {
    return {
      pokemon_current: "",
      pokemon_types: "",
      activeType: "Select A"
    };
  },
  methods: {
    type_click: function(name) {
      this.activeType = name;
      this.retrievePokemonOfSpecifiedType(this.activeType);
    },
    retrievePokemonOfSpecifiedType: function(type) {
      const axios = require("axios");
      const vm = this;

      axios({
        method: "get",
        url: "https://pokeapi.co/api/v2/type/" + type
      }).then(function(response) {
        vm.pokemon_current = response.data.pokemon;
      });
    }
  },
  mounted: function() {
    const axios = require("axios");
    const vm = this;

    this.retrievePokemonOfSpecifiedType(this.activeType);

    axios({
      method: "get",
      url: "https://pokeapi.co/api/v2/type"
    }).then(function(response) {
      vm.pokemon_types = response.data.results;
    });
  }
};
</script>

<style>
</style>
