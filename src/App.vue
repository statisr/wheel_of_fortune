<template>
  <div class="main">
    <button type="button" class="openWheel" @click="wheelState">КНОПКА</button>
    <div class="modalWindow" v-show="openWheel">
      <WheelOfFortune @wheelState="wheelState()" />
    </div>
  </div>
</template>

<script>
import WheelOfFortune from "./components/AnimateBlock.vue";

export default {
  name: "App",
  components: {
    WheelOfFortune,
  },
  data() {
    return {
      openWheel: false,
    };
  },
  methods: {
    wheelState() {
      //console.log(this.openWheel);
      this.openWheel = !this.openWheel;
    },
  },
};
</script>

<style>
.openWheel {
  position: fixed;

  bottom: 35%;
  top: 35%;
  left: 35%;
  right: 35%;
  width: 300px;
  height: 50px;
}
.modalWindow {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 60px;
}
</style>
