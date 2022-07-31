<template>
  <div >
    <vkg  />
    <parent />
  </div>
</template>

<script>
import parent from "./components/parent";
import vkg from "./components/vkg";

export default {
  name: "App",
  components: {
    parent,
    vkg
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
