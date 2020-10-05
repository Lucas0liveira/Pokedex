<template>
  <div class="modal">
    <button @click="showModal = true">Show Modal</button>
    <transition name="fade" appear>
      <div class="modal-overlay" v-if="showModal">AOBA</div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "modal",
  data() {
    return {
      showModal: false
    };
  }
};
</script>

<style>
</style>