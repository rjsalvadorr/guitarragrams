<template>
  <div id="app" class="app">
    <h1 class="app--title">Guitarragrams</h1>
    <p>
      A visual reference for guitar chord voicings,
      built and updated by <a href="http://rj-salvador.com">RJ Salvador</a>.
    </p>
    <PatternGroup :groupData="diagrams.open">
      <p>
        Bacon ipsum dolor amet incididunt sunt kielbasa do turkey pariatur porchetta excepteur fugiat aliquip ea.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.openUpper">
      <p>
        Bacon ipsum dolor amet incididunt sunt kielbasa do turkey pariatur porchetta excepteur fugiat aliquip ea.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.threeString">
      <p>
        Ex voluptate veniam, ham hock salami sirloin aliqua duis nostrud qui.
      </p>
    </PatternGroup>
  </div>
</template>

<script>
import PatternGroup from "./components/PatternGroup.vue";
import chordDiagramsOpenUpper from "./data/chord-diagrams-open-upper.json";
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
        openUpper: chordDiagramsOpenUpper,
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

.app {
  &--title {
    font-size: 5rem;
  }
}

/* Larger than phablet */
@media (min-width: 550px) {
  .app {
    &--title {
      font-size: 6rem;
    }
  }
}
</style>
