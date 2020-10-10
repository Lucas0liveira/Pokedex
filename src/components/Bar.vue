<template>
  <div class="bar-outside" :style="`width: ${300}px`">
    <div
      class="bar-inside"
      :style="
        `width: ${calcBar(value, typeList[type])}px; 
        background-color: ${color};`
      "
    >
      {{ value }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      typeList: {
        hp: 250,
        attack: 134,
        defense: 180,
        speed: 140,
        special: 154,
        weight: 460
      }
    };
  },
  props: {
    type: { type: String, required: true },
    value: { type: Number, required: true },
    color: { type: String, required: true }
  },
  methods: {
    calcBar(value, max) {
      return 300 * (value / max);
    }
  }
};
</script>

<style>
.bar-outside {
  display: flex;
  flex-wrap: wrap;
  height: 24px;
  width: 250px;
  background-color: rgb(192, 192, 192);
  border-radius: 5px;
}
.bar-inside {
  height: 24px;
  border-radius: 5px;
  color: white;
  font-weight: bold;
  text-align: center;
}
</style>