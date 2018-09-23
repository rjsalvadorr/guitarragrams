<template>
  <div id="app">
    <PatternGroup :groupData="diagrams.open" />
    <PatternGroup :groupData="diagrams.threeString" />
    <hr>
    <h4>Debug info (App)</h4>
    <pre>
      <code>{{ `diagrams = ${JSON.stringify(diagrams, null, 2)}` }}</code>
    </pre>
  </div>
</template>

<script>
import PatternGroup from "./components/PatternGroup.vue";
import chordDiagramsOpen from "./data/chord-diagrams-open.json";
import chordDiagrams3string from "./data/chord-diagrams-3string.json";

export default {
  name: "app",
  components: {
    PatternGroup
  },
  data: function() {
    return {
      diagrams: {
        open: chordDiagramsOpen,
        threeString: chordDiagrams3string
      }
    };
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
