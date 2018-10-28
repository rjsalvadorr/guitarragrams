<template>
  <div id="app" class="app">
    <h1 class="app__title">Guitarragrams</h1>
    <div class="row app__intro">
      <div class="five columns">
        <p class="app__description">
          A visual reference for guitar chord voicings,
          built and updated by <a href="http://rj-salvador.com" target="_blank">RJ Salvador</a>.
          Source code can be seen at <a href="https://github.com/rjsalvadorr/guitarragrams" target="_blank">GitHub</a>.
          If you like this kind of nerdy guitar stuff, I have more things <a href="http://www.rj-salvador.com/tags/music/" target="_blank">here</a>.
        </p>
      </div>
      <div class="seven columns">
        <ul class="app__notes">
          <li>
            <span>
              Click the help tab (on the left) to see the table of contents and legend.
            </span>
          </li>
          <li>
            <span>
              The chord diagrams are only for standard tuning (for now).
            </span>
          </li>
          <li>
            <span>
              No open strings are used here.
              These chord patterns are meant to be usable on any position on the fretboard.
            </span>
          </li>
          <li>
            <span>
              Planned features: chord playback, diagram filtering/sorting, left-hand mode, alternate tunings.
            </span>
          </li>
        </ul>
      </div>
    </div>

    <PatternGroup :groupData="diagrams.open" customId="open-voicings">
      <p class="pattern-group__description">
        Chord voicings with with plenty of space between the notes.
        These can be useful for playing on two areas of the fretboard at the same time.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.openUpper"></PatternGroup>

    <hr>

    <PatternGroup :groupData="diagrams.melodicLower" customId="melodic-voicings">
      <p class="pattern-group__description">
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
      <p class="pattern-group__description">
        Eiusmod minim voluptate tempor, picanha sed ball tip. Consequat enim shoulder ut pork loin.
      </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.fourStringMiddle"></PatternGroup>
    <PatternGroup :groupData="diagrams.fourStringUpper"></PatternGroup>

    <hr>

    <PatternGroup :groupData="diagrams.seventhsMaj" customId="seventh-chord-patterns">
      <p class="pattern-group__description">
        Shoulder short ribs excepteur boudin anim ham hock andouille. Jowl culpa ball tip nostrud alcatra pork chop.
     </p>
    </PatternGroup>
    <PatternGroup :groupData="diagrams.seventhsMin"></PatternGroup>
    <PatternGroup :groupData="diagrams.seventhsDim"></PatternGroup>

    <hr>

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
import seventhsMaj from "./data/7ths-major.json";
import seventhsMin from "./data/7ths-minor.json";
import seventhsDim from "./data/7ths-diminished.json";

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
        seventhsMaj: seventhsMaj,
        seventhsMin: seventhsMin,
        seventhsDim: seventhsDim
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
  margin-top: 30px;
}

pre,
code {
  text-align: left;
}

.app {
  hr {
    margin: 0 0 5rem 0;
    border-color: $main-color;
  }

  &__title {
    text-align: center;
  }

  &__description,
  &__notes {
    text-align: left;
  }

  &__title,
  &__description,
  &__notes {
    padding: 0;
  }

  .bm-menu {
    padding-top: 3rem;
  }

  .bm-menu--open {
    border: none;
    box-shadow: $mui-box-shadow;
  }

  .cross-style {
    right: 10px;
    color: #ffffff;

    .bm-cross {
      height: 20px !important;
      background-color: #ffffff !important;
    }
  }

  .bm-burger-button {
    position: fixed;
    top: 0;
    left: 0;
    background-color: rgb(63, 63, 65);
    height: auto;
    width: auto;
    padding: 0 10px;
    border-radius: 0 0 10px 0;
    &::after {
      content: "\f128";
      color: #ffffff;
      font-family: FontAwesome;
      font-size: 30px;
    }
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
/* Larger than mobile */
@media (min-width: 400px) {
  #app {
    margin-top: 40px;
  }
  .app {
    hr {
      margin: 0 20px 5rem 20px;
    }
    .bm-burger-button {
      padding: 2px 10px;
      &::after {
        font-size: 35px;
      }
    }
    &__title,
    &__description,
    &__notes {
      padding: 0 20px;
    }
    &__title {
      text-align: left;
    }
  }
}
/* Larger than phablet */
@media (min-width: 550px) {
  #app {
    margin-top: 60px;
  }
  .app {
    &__intro {
      margin-bottom: 20px;
    }
    &__title {
      font-size: 6rem;
    }
    .bm-burger-button {
      top: calc(50% - 100px);
      border-radius: 0 8px 8px 0;
      padding: 15px;
      &::after {
        font-size: 40px;
      }
    }
  }
}
</style>
