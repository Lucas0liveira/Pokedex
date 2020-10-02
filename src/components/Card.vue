<template>
  <div class="card">
    <div class="pokemon">
      <p class="id">#{{ number }}</p>
      <div class="image">
        <img
          class="imgPoke"
          :alt="name"
          :src="
            `https://raw.githubusercontent.com/ZeChrales/PogoAssets/master/pokemon_icons/pokemon_icon_${image}_00.png`
          "
          style="max-width: 100%; max-height: 100%; display:block;"
        />
      </div>
    </div>

    <p class="nomePoke">{{ name }}</p>

    <div class="tipos">
      <p class="tipo">{{ type1 }}</p>
      <p class="tipo">{{ type2 }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: { type: String, required: true },
    type1: { type: String },
    type2: { type: String },
    image: { type: String, required: true },
    number: { type: String, required: true }
  }
};
</script>

<style>
.card {
  display: flex;
  flex-direction: column;
  width: 196px;
  height: 280px;
  border: solid 2px #666666;
  border-radius: 5px;
  background-color: #ffffff;
  margin: 12px;
}
.card:hover {
  transform: translateY(-8px);
  box-shadow: #d3d3d3 8px 8px 1px;
}
.pokemon {
  background-color: rgb(204, 204, 204);
  height: 100vh;
  border-radius: 5px;
  border-bottom: solid 1px #141414;
  padding: 8px;
}
.image {
  display: flex;
  justify-content: center;
  align-items: center;
  max-height: 120px;
}
.nomePoke {
  text-align: center;
  font-size: 20px;
  margin-bottom: 8px;
}
.tipo {
  background-color: #ff4b3e;
  border-radius: 8px;
  margin: 6px;
  padding: 5px;
  font-size: 15px;
  font-weight: 500;
}
.tipos {
  display: flex;
  justify-content: center;
}
.id {
  margin: 0px;
  font-weight: bold;
  color: #141414;
}
</style>