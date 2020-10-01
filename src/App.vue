<template>
  <div class="container">
    <div class="title">
      <h1>Pokedex</h1>
    </div>
    <div class="pokemons">
      <Card />
      <div>
        <p v-for="(p, index) in pokemonList" :key="index">{{ p.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../src/components/Card";
export default {
  created() {
    this.fetchPokemon();
  },
  data() {
    return {
      pokemonList: []
    };
  },
  name: "App",
  components: { Card },
  methods: {
    fetchPokemon() {
      const pendentes = [];
      for (var n = 1; n < 151; n++) {
        pendentes.push(
          fetch(`https://pokeapi.co/api/v2/pokemon/${n}`).then(response =>
            response.json()
          )
        );
      }
      Promise.all(pendentes).then(pokemons => {
        this.pokemonList = pokemons;
        console.log(this.pokemonList);
      });
    }
  }
};
</script>

<style>
body {
  background-color: rgb(66, 142, 255);
  font-family: "Roboto", sans-serif;
}

.container {
  padding: 32px;
  max-width: 1200px;
  height: 100vh;
}
.title {
  display: flex;
  justify-content: center;
  background-color: white;
  border-radius: 5px;
  width: 100vh;
  margin-bottom: 64px;
}

.pokemons {
  display: flex;
  justify-content: center;
  background-color: white;
  border-radius: 5px;
  width: 100vh;
  height: auto;
}

#app {
  display: flex;
  justify-content: center;
}
</style>
