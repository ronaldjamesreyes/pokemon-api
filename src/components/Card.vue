<template>
    <div class="col-3">
        <div class="card" style="width: 18rem;">
            <img v-bind:src="pokemon.sprites.front_shiny" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title text-capitalize">{{pokemon.name}}</h5>
                <p class="pokemon-height">Height: {{pokemon.height*3.937}} units <br> Weight: {{pokemon.weight}} units</p>
            </div>
        </div>
    </div>
</template>


<script>
export default {
  name: 'Card',
  data: function(){
      return{
          pokemon:""
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
.card{
    text-align: center;
    margin-bottom: 10px;
}
</style>
