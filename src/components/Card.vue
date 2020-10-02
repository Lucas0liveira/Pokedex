<template>
  <div :class="cardClass" @Click="expand" @blur="expand">
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
      typeList: []
    };
  },
  props: {
    name: { type: String, required: true },
    types: { type: Array },
    image: { type: String, required: true },
    number: { type: String, required: true }
  },
  methods: {
    getTypes() {
      for (var i = 0; i < this.types.length; i++) {
        this.typeList.push(this.types[i].type.name);
      }
    },
    expand() {
      if (this.cardClass === "card") {
        this.cardClass = "expanded";
      } else {
        this.cardClass = "card";
      }
    }
  },
  created() {
    this.getTypes();
    console.log(this.typeList);
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
.expanded {
  display: flex;
  flex-direction: column;
  width: 392px;
  height: 560px;
  border: solid thin #cecece;
  border-radius: 5px;
  background-color: #ffffff;
  margin: 12px;
  box-shadow: #d3d3d3 8px 8px 1px;
  transition: 0.5s;
}
.card:hover {
  transform: translateY(-8px);
}
.pokemon {
  background-color: rgb(204, 204, 204);
  height: 100vh;
  max-height: 196px;
  border-radius: 2px;
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