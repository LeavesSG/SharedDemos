<template>
  <document></document>
</template>

<script>
import Document from "./components/Document.vue";

export default {
  name: "App",
  components: {
    Document,
  },
};
</script>

<style>
body{
  width: 100vw;
  margin: 0;
}

#app {
  width: 100%;
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #2c3e50;
  padding: 1%;
}
</style>
