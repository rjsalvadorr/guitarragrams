<template>
  <div id="app" class="app">
    <h1 class="app--title">Guitarragrams</h1>
    <p>
      A visual reference for guitar chord voicings,
      built and updated by <a href="http://rj-salvador.com" target="_blank">RJ Salvador</a>.<br>
      Source code <a href="https://github.com/rjsalvadorr/guitarragrams" target="_blank">can be seen here</a>.
      If you like this kind of nerdy guitar stuff, I have more things <a href="http://www.rj-salvador.com/tags/music/" target="_blank">here</a>.
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
    <PatternGroup :groupData="diagrams.melodicUpper">
      <p>
        Ex voluptate veniam, ham hock salami sirloin aliqua duis nostrud qui.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.melodicMiddle">
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
import chordDiagrams3string from "./data/melodic-upper.json";
import melodicMiddle from "./data/melodic-middle.json";

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
        melodicUpper: chordDiagrams3string,
        melodicMiddle: melodicMiddle
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
