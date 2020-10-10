<template>
  <div :class="cardClass">
    <div class="pokemon" :style="`background-color: ${bgColors[typeList[0]]}`">
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

    <p class="nomePoke" style="margin-top: 12px">{{ name }}</p>

    <div class="tipos">
      <p :class="`tipo ${t}`" v-for="(t, index) in typeList" :key="index">
        {{ t }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardClass: "card",
      typeList: [],
      bgColors: {
        poison: "#ba84e0",
        grass: "#ade084",
        fire: "#e0b784",
        water: "#84b8e0",
        bug: "#84e092",
        normal: "#d9d9d9",
        electric: "#ede098",
        fairy: "#e693c1",
        ground: "#edc098",
        fighting: "#f05965",
        psychic: "#ff8299",
        rock: "#c9a28b",
        ice: "#6bc6d6",
        ghost: "#424587",
        dragon: "#debd6f"
      }
    };
  },
  props: {
    name: { type: String, required: true },
    types: { type: Array },
    image: { type: String, required: true },
    number: { type: Number, required: true }
  },
  methods: {
    getTypes() {
      for (var i = 0; i < this.types.length; i++) {
        this.typeList.push(this.types[i].type.name);
      }
    }
  },
  created() {
    console.log(this.bgColors[this.typeList[1]]);
    this.getTypes();
  }
};
</script>

<style>
.card {
  display: flex;
  flex-direction: column;
  width: 196px;
  height: 280px;
  border: solid thin #cecece;
  border-radius: 5px;
  background-color: #ffffff;
  margin: 12px;
  transition: 0.5s;
}
.id {
  background-color: #f3f3f3;
  border-radius: 16px;
  color: #141414;
  width: 48px;
  text-align: center;
  position: absolute;
  box-shadow: #505050 4px 4px 2px;
}
.card:hover {
  transform: translateY(-8px);
  box-shadow: #929292 8px 8px 1px;
}
.pokemon {
  display: flex;
  flex-wrap: wrap;
  background-color: rgb(204, 204, 204);
  height: 100vh;
  max-height: 196px;
  border-radius: 2px;
  padding: 8px;
  background-size: cover;
}
.image {
  display: flex;
  justify-content: center;
  align-items: center;
  max-height: 188px;
}
.nomePoke {
  text-align: center;
  font-size: 20px;
  margin-bottom: 8px;
}
.tipos {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.tipo {
  border-radius: 16px;
  margin: 6px;
  padding: 5px;
  font-size: 15px;
  font-weight: 500;
  width: 48px;
  text-align: center;
}
.poison {
  background-color: rgb(179, 0, 202);
  color: white;
}
.grass {
  background-color: rgb(0, 197, 0);
  color: white;
}
.fire {
  background-color: rgb(255, 86, 20);
  color: white;
}
.flying {
  background-color: rgb(172, 198, 255);
  color: rgb(255, 255, 255);
}
.water {
  background-color: rgb(0, 183, 255);
  color: whitesmoke;
}
.bug {
  background-color: yellowgreen;
  color: whitesmoke;
}
.normal {
  background-color: grey;
  color: whitesmoke;
}
.electric {
  background-color: rgb(255, 167, 4);
  color: whitesmoke;
}
.ground {
  background-color: rgb(184, 110, 0);
  color: whitesmoke;
}
.fairy {
  background-color: rgb(255, 88, 219);
  color: whitesmoke;
}
.fighting {
  background-color: rgb(197, 0, 0);
  color: whitesmoke;
}
.psychic {
  background-color: rgb(255, 97, 92);
  color: whitesmoke;
}
.rock {
  background-color: rgb(129, 89, 82);
  color: whitesmoke;
}
.ice {
  background-color: rgb(86, 190, 177);
  color: whitesmoke;
}
.steel {
  background-color: rgb(0, 31, 77);
  color: whitesmoke;
}
.ghost {
  background-color: rgb(59, 0, 136);
  color: whitesmoke;
}
.dragon {
  background-color: rgb(184, 120, 36);
  color: whitesmoke;
}
.id {
  margin: 0px;
  font-weight: bold;
  color: #141414;
}
</style>
