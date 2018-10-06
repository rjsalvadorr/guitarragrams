<template>
  <div id="app" class="app">
    <h1 class="app__title">Guitarragrams</h1>
    <p class="app__description">
      A visual reference for guitar chord voicings,
      built and updated by <a href="http://rj-salvador.com" target="_blank">RJ Salvador</a>.<br>
      Source code <a href="https://github.com/rjsalvadorr/guitarragrams" target="_blank">can be seen here</a>.
      If you like this kind of nerdy guitar stuff, I have more things <a href="http://www.rj-salvador.com/tags/music/" target="_blank">here</a>.
    </p>

    <PatternGroup :groupData="diagrams.open" customId="open-voicings">
      <p>
        Chord voicings with with plenty of space between the notes.
        These can be useful for playing on two areas of the fretboard at the same time.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.openUpper"></PatternGroup>

    <hr>

    <PatternGroup :groupData="diagrams.melodicLower" customId="melodic-voicings">
      <p>
        These voicings are useful for adding harmony
        to a melodic passage. Technically, they're also efficient.
        Your fretting hand can form these chord shapes
        quickly, and you can move through most chords while barely
        moving your hand around the neck.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.melodicMiddle"></PatternGroup>
    <PatternGroup :groupData="diagrams.melodicUpper"></PatternGroup>

    <hr>

    <PatternGroup :groupData="diagrams.fourStringLower" customId="four-string-patterns">
      <p>
        Eiusmod minim voluptate tempor, picanha sed ball tip. Consequat enim shoulder ut pork loin.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.fourStringMiddle"></PatternGroup>
    <PatternGroup :groupData="diagrams.fourStringUpper"></PatternGroup>

    <hr>

    <PatternGroup :groupData="diagrams.seventhsLower" customId="seventh-chord-patterns">
      <p>
        Shoulder short ribs excepteur boudin anim ham hock andouille. Jowl culpa ball tip nostrud alcatra pork chop.
     </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.seventhsMiddle"></PatternGroup>
    <PatternGroup :groupData="diagrams.seventhsUpper"></PatternGroup>

    <Slide
      @openMenu="handleOpenMenu"
      @closeMenu="handleCloseMenu"
    >
      <DrawerPanel />
    </Slide>
  </div>
</template>

<script>
import { Slide } from "vue-burger-menu";

import PatternGroup from "./components/PatternGroup.vue";
import FretboardMarker from "./components/FretboardMarker.vue";
import DrawerPanel from "./components/DrawerPanel.vue";

import chordDiagramsOpenUpper from "./data/chord-diagrams-open-upper.json";
import chordDiagramsOpen from "./data/chord-diagrams-open.json";
import chordDiagrams3string from "./data/melodic-upper.json";
import melodicMiddle from "./data/melodic-middle.json";
import melodicLower from "./data/melodic-lower.json";
import fourStringLower from "./data/four-string-lower.json";
import fourStringMiddle from "./data/four-string-middle.json";
import fourStringUpper from "./data/four-string-upper.json";
import seventhsLower from "./data/7ths-lower.json";
import seventhsMiddle from "./data/7ths-middle.json";
import seventhsUpper from "./data/7ths-upper.json";

export default {
  name: "app",
  components: {
    Slide,
    PatternGroup,
    FretboardMarker,
    DrawerPanel
  },
  data: function() {
    return {
      diagrams: {
        openUpper: chordDiagramsOpenUpper,
        open: chordDiagramsOpen,
        melodicUpper: chordDiagrams3string,
        melodicMiddle: melodicMiddle,
        melodicLower: melodicLower,
        fourStringLower: fourStringLower,
        fourStringMiddle: fourStringMiddle,
        fourStringUpper: fourStringUpper,
        seventhsLower: seventhsLower,
        seventhsMiddle: seventhsMiddle,
        seventhsUpper: seventhsUpper
      }
    };
  },
  methods: {
    handleOpenMenu: function() {
      document.querySelector(".bm-menu").classList.add("bm-menu--open");
      document.querySelector(".bm-menu").classList.remove("bm-menu--closed");
    },
    handleCloseMenu: function() {
      document.querySelector(".bm-menu").classList.add("bm-menu--closed");
      document.querySelector(".bm-menu").classList.remove("bm-menu--open");
    }
  }
};
</script>

<style lang="scss">
$box-shadow-color: rgba(0, 0, 0, 0.5);
$mui-box-shadow: 0 10px 20px rgba(0, 0, 0, 0.38), 0 6px 6px rgba(0, 0, 0, 0.46);
$main-color: #2c3e50;

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $main-color;
  margin-top: 60px;
}

pre,
code {
  text-align: left;
}

.app {
  hr {
    margin: 0 20px 5rem 20px;
    border-color: $main-color;
  }

  &__title,
  &__description {
    text-align: left;
    padding-left: 20px;
  }

  .bm-menu {
    padding-top: 3rem;
  }

  .bm-menu--open {
    border: none;
    // box-shadow: -1px 0px 5px 5px $box-shadow-color;
    box-shadow: $mui-box-shadow;
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
      color: #ffffff;
      font-family: FontAwesome;
      font-size: 40px;
    }
    // box-shadow: 2px 2px 10px 1px $box-shadow-color;
    box-shadow: $mui-box-shadow;
    z-index: 999;
  }

  .bm-item-list {
    margin-left: 0;
  }

  .bm-burger-bars.line-style {
    display: none;
  }
}

/* Larger than phablet */
@media (min-width: 550px) {
  .app {
    &__title {
      font-size: 6rem;
    }
  }
}
</style>
