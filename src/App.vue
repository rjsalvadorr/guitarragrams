<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <hr>
    <h1>Debug info</h1>
    <pre>
      <code>{{ `diagrams = ${JSON.stringify(diagrams, null, 2)}` }}</code>
    </pre>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import chordDiagramsOpen from "./data/chord-diagrams-open.json";
import chordDiagrams3string from "./data/chord-diagrams-3string.json";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  data: function() {
    return {
      diagrams: {
        open: chordDiagramsOpen,
        '3string': chordDiagrams3string
      }
    }
  }
};

</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

pre,
code {
  text-align: left;
}
</style>
