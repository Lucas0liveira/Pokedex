<template>
  <div class="container">
    <div class="title">
      <h1>Pokedex</h1>
    </div>
    <div class="pokemons">
      <Card />
    </div>
  </div>
</template>

<script>
import Card from "../src/components/Card";
export default {
  name: "App",
  components: { Card }
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
  border-radius: 8px;
  width: 90vh;
  margin-bottom: 64px;
}

.pokemons {
  display: flex;
  justify-content: center;
  background-color: white;
  border-radius: 8px;
  width: 90vh;
}

#app {
  display: flex;
  justify-content: center;
}
</style>
