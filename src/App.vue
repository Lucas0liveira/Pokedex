<template>
  <div class="container">
    <div class="title">
      <h1>Pokedex</h1>
    </div>
    <div class="pokemons">
      <div
        class="poke"
        @click="summonModal(index)"
        v-for="(p, index) in pokemonList"
        :key="index"
      >
        <Card
          :name="p.name.toUpperCase()"
          :image="adjustIndex(index + 1)"
          :types="p.types"
          :number="index + 1"
        />
      </div>
      <div v-if="showModal" class="modal">
        <Modal
          :pokeId="pokeId"
          :pokemon="pokemonList[pokeId]"
          :image="adjustIndex(pokeId + 1)"
          :types="pokemonList[pokeId].types"
        />
        <button class="modal-btn" @click="showModal = false">
          <img
            src="./assets/close.png"
            alt="Close button"
            style="height:64px"
          />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../src/components/Card";
import Modal from "../src/components/Modal";
export default {
  created() {
    this.fetchPokemon();
  },
  data() {
    return {
      pokemonList: [],
      showModal: false,
      pokeId: 0
    };
  },
  name: "App",
  components: { Card, Modal },
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
    },
    summonModal(id) {
      console.log(this.showModal);
      this.showModal = true;
      this.pokeId = id;
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
  align-items: center;
  flex-wrap: wrap;
  background-color: rgb(255, 255, 255);
  border-radius: 5px;
  height: auto;
}

.modal-btn {
  position: fixed;
  top: 10vh;
  left: 80%;
  background: none;
  border: none;
  transition: 0.2s;
}

.modal-btn:hover {
  cursor: pointer;
  opacity: 70%;
}

#app {
  display: flex;
  justify-content: center;
}
</style>
