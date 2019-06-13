<template>
    <div>
        <div class="card" style="width: 18rem;">
            <img v-bind:src="pokemon.sprites.front_default" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{pokemon.name}}</h5>
                <p class="pokemon-height">Height: {{pokemon.height*3.937}} units <br> Weight: {{pokemon.weight}} units</p>
            </div>
        </div>

<div class="container">
    <div class="row">
      <div class="col-sm">
        <div class="card" style="width: 18rem;">
            <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/25.png" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{pokemon.name}}</h5>
                <p class="pokemon-height">Height: {{pokemon.height}} <br> Weight: {{pokemon.weight}}</p>
            </div>
        </div>
    </div>
    <div class="col-sm">
        <div class="card" style="width: 18rem;">
            <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/26.png" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{pokemon.name}}</h5>
                <p class="pokemon-height">Height: {{pokemon.height}} <br> Weight: {{pokemon.weight}}</p>
            </div>
        </div>
    </div>
    <div class="col-sm">
        <div class="card" style="width: 18rem;">
            <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/172.png" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{pokemon.name}}</h5>
                <p class="pokemon-height">Height: {{pokemon.height}} <br> Weight: {{pokemon.weight}}</p>
            </div>
        </div>
    </div>
  </div>
</div>


    </div>
</template>


<script>
export default {
  name: 'Card',
  data: function(){
      return{
          pokemon:null
      }
  },
  props: {
    msg: String
  },
  mounted: function(){
    console.log("mounted function ran")

    const axios = require('axios');
    const vm = this;

    axios({
        method: 'get',
        url: 'https://pokeapi.co/api/v2/pokemon/pikachu',
         responseType: 'stream'
    })
    .then(function (response){
        console.log(response.data);
        vm.pokemon = response.data
    });

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
