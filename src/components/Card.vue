<template>
    <div class="col-md-4" v-if="pokemon.sprites && pokemon.sprites.front_shiny">
        <div class="card" style="width: 18rem;">
            <img v-bind:src="pokemon.sprites.front_shiny" class="card-img-top" alt="..." />
            <div class="card-body">
                <h5 class="card-title text-capitalize">{{pokemon.name}}</h5>
                <p>Height: {{pokemon.height*4.0.toFixed(2)}} Inches</p>
                <p>Weight: {{pokemon.weight*1.0.toFixed(2)}} Pounds</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "Card",
  data: function() {
    return {
      pokemon: ""
    };
  },
  props: {
    url: String
  },
  mounted: function() {
    const axios = require("axios");
    const vm = this;

    axios({
      method: "get",
      url: vm.url,
      responseType: "stream"
    }).then(function(response) {
      vm.pokemon = response.data;
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
<<<<<<< HEAD
.card {
  margin-top: 20px;
  text-align: center;
  margin-bottom: 20px;
  border: 3px solid #007bff;
  border-radius: 15px;
=======
.card{
    text-align: center;
    margin-bottom: 20px;
>>>>>>> parent of a029668... adding card borders
}
</style>
