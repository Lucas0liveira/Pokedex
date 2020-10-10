<template>
  <div class="modal">
    <transition name="fade" appear>
      <div class="modal-overlay" :style="`border: solid 8px ${color}`">
        <div class="containerPoke">
          <div class="viewPoke">
            <div class="cardPoke">
              <h1 class="idPoke">#{{ pokeId + 1 }}</h1>
              <div>
                <img
                  :alt="name"
                  :src="
                    `https://raw.githubusercontent.com/ZeChrales/PogoAssets/master/pokemon_icons/pokemon_icon_${image}_00.png`
                  "
                  style="max-width: 100%; max-height: 100%; display:block;"
                />
              </div>
            </div>
            <div class="descPoke">
              <h1 class="namePoke">{{ pokemon.name.toUpperCase() }}</h1>
              <div class="tipos">
                <p
                  :class="`tipo ${t}`"
                  v-for="(t, index) in typeList"
                  :key="index"
                >
                  {{ t }}
                </p>
              </div>
            </div>
          </div>

          <div class="statsPoke">
            <h1 class="stats">STATISTICS</h1>
            <div class="stat">
              <h3>HP:</h3>
              <Bar
                type="hp"
                :value="pokemon.stats[0].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>ATTACK:</h3>
              <Bar
                type="attack"
                :value="pokemon.stats[1].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>DEFENSE:</h3>
              <Bar
                type="defense"
                :value="pokemon.stats[2].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>SPECIAL ATTACK:</h3>
              <Bar
                type="special"
                :value="pokemon.stats[3].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>SPECIAL DEFENSE:</h3>
              <Bar
                type="special"
                :value="pokemon.stats[4].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>SPEED:</h3>
              <Bar
                type="speed"
                :value="pokemon.stats[5].base_stat"
                :color="color"
              />
            </div>
            <div class="stat">
              <h3>WEIGHT:</h3>
              <Bar type="weight" :value="pokemon.weight / 10" :color="color" />
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import Bar from "./Bar";
export default {
  name: "modal",
  data() {
    return {
      typeList: [],
      bgColors: {
        poison: "rgb(179, 0, 202)",
        grass: "rgb(0, 197, 0)",
        fire: "rgb(255, 86, 20)",
        water: "rgb(0, 183, 255)",
        bug: "yellowgreen",
        normal: "grey",
        electric: "rgb(255, 167, 4)",
        fairy: "rgb(255, 88, 219)",
        ground: "rgb(184, 110, 0)",
        fighting: " rgb(197, 0, 0)",
        psychic: "rgb(255, 97, 92)",
        rock: "rgb(129, 89, 82)",
        ice: "rgb(86, 190, 177)",
        ghost: "rgb(59, 0, 136)",
        dragon: "rgb(184, 120, 36)"
      },
      color: ""
    };
  },
  components: {
    Bar
  },
  props: {
    pokeId: { type: Number, required: true },
    pokemon: { type: Object, required: true },
    image: { type: String, required: true },
    types: { type: Array }
  },

  methods: {
    getTypes() {
      for (var i = 0; i < this.types.length; i++) {
        this.typeList.push(this.types[i].type.name);
      }
      this.color = this.bgColors[this.typeList[0]];
    }
  },
  created() {
    this.getTypes();
  }
};
</script>

<style>
.modal {
  position: fixed;
  top: 0px;
  left: 0px;
  height: 100%;
  width: 100%;
  background-color: #1818188e;
}
.modal-overlay {
  margin: 23vh auto;
  width: 1000px;
  height: 440px;
  border-radius: 5px;
  background-color: #ffffff;
  padding: 16px;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
.containerPoke {
  display: flex;
  width: 100%;
  height: 100%;
  column-gap: 3vw;
  flex-wrap: wrap;
}
.viewPoke {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  margin-top: 5px;
}
.cardPoke {
  display: flex;
  flex-direction: column;
  width: 280px;
  background-image: url("../assets/fundo1.jpg");
  background-size: cover;
  border-radius: 8px;
  box-shadow: #c4c4c4 5px 5px 1px;
  margin-bottom: 16px;
}
.descPoke {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  margin-top: 5px;
  justify-self: flex-end;
  align-items: center;
  height: 120px;
  border-radius: 8px;
  box-shadow: #c4c4c4 5px 5px 1px;
}
.idPoke {
  background-color: #f3f3f3;
  border-radius: 16px;
  color: #141414;
  width: 64px;
  height: 24px;
  text-align: center;
  font-size: 1.2rem;
  position: absolute;
  margin-left: 12px;
}
.namePoke {
  color: #505050;
  margin-bottom: 12px;
}
.statsPoke {
  display: flex;
  flex-direction: column;
  width: 512px;
  border-left: solid 3px #c4c4c4;
}
.stats {
  align-self: center;
  color: #141414;
}
.stat {
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.stat .Bar {
  justify-self: flex-end;
}
h3 {
  margin: 10px;
  color: #141414;
}
</style>
