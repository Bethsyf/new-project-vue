<template>
  <HomeV first-name="Bethsy" last-name="Falcon" otro="algo"></HomeV>
</template>

<script>
import HomeV from "./components/HomeV.vue";
import { provide } from "vue"

export default {
  name: "App",
  components: {
    HomeV,
  },
  setup() {
    provide("userName", "Bethsyf");
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>