<template>
  <h1>POKEDEX</h1>
  <Card />
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
  background-color: rgb(255, 221, 190);
}
</style>
