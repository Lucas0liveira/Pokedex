<template>
  <div class="container">
    <div class="title">
      <h1>Pokedex</h1>
    </div>
    <div class="pokemons">
      <Card
        v-for="(p, index) in pokemonList"
        :key="index"
        :name="p.name.toUpperCase()"
        :image="adjustIndex(index + 1)"
        type1="Grass"
        type2="Poison"
        :number="index + 1"
      />
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
    },
    adjustIndex(index) {
      if (index < 10) {
        return `00${index}`;
      } else if (index < 100) {
        return `0${index}`;
      } else {
        return `${index}`;
      }
    }
  }
};
</script>

<style>
body {
  font-family: "Roboto", sans-serif;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #6b00b3);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  background-attachment: fixed;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.container {
  padding: 32px;
  max-width: 1440px;
  height: 100vh;
}
.title {
  display: flex;
  justify-content: center;
  background-color: white;
  border-radius: 5px;
  margin-bottom: 64px;
}

.pokemons {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  background-color: white;
  border-radius: 5px;
  height: auto;
}

#app {
  display: flex;
  justify-content: center;
}
</style>
