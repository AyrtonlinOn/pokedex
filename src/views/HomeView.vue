<script setup>
//props - onMounted, reactive, ref
import { onMounted, reactive, ref } from 'vue';
import ListPokemons from '../components/ListPokemons.vue';

let pokemons = reactive(ref())

//fetch - axios
onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=20%offset=0")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results
    console.log(pokemons)
  });
})

</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <div class="card" style="width: 18rem;">
            <img src="https://assets.pokemon.com/assets/cms2/img/pokedex/full/025.png" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Card Title</h5>
            <p class="card-text">Um texto resumido e pequeno aqui</p>
          </div>
        </div>
        </div>
        <div class="col-sm-12 col-md-6">
          <div class="card" style="width: 18rem">
            <ul class="list-group">
              <li class="list-group-item" v-for="pokemon in pokemons" :key="pokemon.name">
                {{ pokemon.name }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
