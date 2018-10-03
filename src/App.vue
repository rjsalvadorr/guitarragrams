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
    <PatternGroup :groupData="diagrams.melodicLower">
      <p>
        These same patterns apply to the bottom 3 strings as well.
      </p>
    </PatternGroup>

    <Slide>
      <div class="rj-menu-wrapper">
        <h2>Help</h2>
        <p>Tail swine culpa spare ribs cupim consectetur ut. Eiusmod minim voluptate tempor, picanha sed ball tip. Consequat enim shoulder ut pork loin. Dolore ut beef cow buffalo kielbasa dolor corned beef consectetur sint.</p>
      </div>
    </Slide>
  </div>
</template>

<script>
import { Slide } from 'vue-burger-menu'

import PatternGroup from "./components/PatternGroup.vue";
import chordDiagramsOpenUpper from "./data/chord-diagrams-open-upper.json";
import chordDiagramsOpen from "./data/chord-diagrams-open.json";
import chordDiagrams3string from "./data/melodic-upper.json";
import melodicMiddle from "./data/melodic-middle.json";
import melodicLower from "./data/melodic-lower.json";

export default {
  name: "app",
  components: {
    PatternGroup,
    Slide
  },
  data: function() {
    return {
      diagrams: {
        openUpper: chordDiagramsOpenUpper,
        open: chordDiagramsOpen,
        melodicUpper: chordDiagrams3string,
        melodicMiddle: melodicMiddle,
        melodicLower: melodicLower
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

  .bm-burger-button {
    position: fixed;
    top: calc(50% - 100px);
    left: 0;
    background-color: rgb(63, 63, 65);
    height: auto;
    width: auto;
    padding: 15px;
    border-radius: 0 8px 8px 0;
    &::after {
      content: "\f128";
      color: #FFFFFF;
      font-family: FontAwesome;
      font-size: 40px;
    }
    box-shadow: 2px 2px 10px 1px rgba(0, 0, 0, 0.33);
    z-index: 999;
  }

  .bm-item-list {
    margin-left: 0;
  }

  .bm-burger-bars.line-style {
    display: none;
  }

  .cross-style {
    right: 8px;
    color: #FFFFFF;

    .bm-cross {
      background-color: #FFFFFF;
    }
  }

  .rj-menu-wrapper {
    width: 300px;
    display: block;
    box-sizing: border-box;
    color: #FFFFFF;
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
