<template>
    <div class="col-md-4" v-if="pokemon.sprites && pokemon.sprites.front_shiny">
        <div class="card" style="width: 18rem;">
            <img v-bind:src="pokemon.sprites.front_shiny" class="card-img-top" alt="..." />
            <div class="card-body">
                <h5 class="card-title text-capitalize">{{pokemon.name}}</h5>
                <p>Height: {{pokemon.height}} Inches</p>
                <p>Weight: {{pokemon.weight}} Pounds</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Card',
  data: function(){
      return{
          pokemon: ""
      }
  },
  props: {
    url: String
  },
  mounted: function(){
    console.log("mounted function ran")

    const axios = require('axios');
    const vm = this;

    axios({
        method: 'get',
        url: vm.url,
        responseType: 'stream'
    })
    .then(function (response){
        vm.pokemon = response.data
    });

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.Card {
    margin-top: 20px;
    text-align: center;
    margin-bottom: 20px;
    border: 3px solid #007bff;
    border-radius: 15px;
}
</style>
