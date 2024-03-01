<template>
<div>
  <ModalButton/>  
</div>
</template>

<script>
import ModalButton from  "./components/ModalButton.vue";
export default {
  name: "App",
  components: {
    ModalButton
  },
  data() {
    return{
      show: false,
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
