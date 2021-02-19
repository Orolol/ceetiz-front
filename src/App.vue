<template>
  <div id="app">
    <FormEnt />
  </div>
</template>

<script>
import FormEnt from "./components/FormEnt.vue"

export default {
  name: "App",
  components: {
    FormEnt
  }
}
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
