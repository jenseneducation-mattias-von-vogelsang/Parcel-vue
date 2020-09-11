<template>
  <div id="app">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msg: "Hurray! ParcelJS Zero Config Vue app is running!",
    };
  },
};
</script>

<style>
#app {
  color: red;
}
</style>