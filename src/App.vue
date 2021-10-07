<template>
  <div id="app">
    <img id="image" alt="Vue logo" src="./assets/logo.png" />
    <Container />
  </div>
</template>

<script>
import Container from "./components/Container.vue";
export default {
  name: "App",
  components: {
    Container,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  background-color: blue;
  width: 100%;
}

body {
  background-color: darkblue;
}

#image {
  width: 20%;
  padding: 2rem;
}
</style>
