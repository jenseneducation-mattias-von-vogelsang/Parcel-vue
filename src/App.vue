<template>
  <div id="app">
    <h1>{{ msg }}</h1>
    <Gif />
  </div>
</template>

<script>
import Gif from "./components/Gif.vue";
export default {
  name: "app",
  data() {
    return {
      msg: "Hurray! ParcelJS Zero Config Vue app is running!",
    };
  },
  components: {
    Gif,
  },
};
</script>

<style>
#app {
  color: red;
}
</style>
