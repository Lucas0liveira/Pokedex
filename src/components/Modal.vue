<template>
  <div class="modal">
    <transition name="fade" appear>
      <div class="modal-overlay">
        <h1>{{ pokeId }}</h1>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "modal",
  props: {
    pokeId: { type: Number, required: true }
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
  margin: 25vh auto;
  width: 960px;
  height: 720px;
  border-radius: 5px;
  border: ridge 8px #ff5555;
  background-color: #ffffff;
  padding: 16px;

  display: flex;
  flex-direction: column;
}
</style>
