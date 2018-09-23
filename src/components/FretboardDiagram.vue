<template>
  <div class="fretboard-diagram">
    <span>{{ label }}</span>
    <slot></slot>
    <div :class="['fretboard', 'fretboard--' + instrument]">
      <div v-for="n in strings" :key="n" :class="['string', 'string--' + n]">
        <div v-for="m in frets" :key="m" :class="['fret', 'fret--' + m]">
          <FretboardMarker :markerData="markers" :stringNum="n" :fretNum="m"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FretboardMarker from "./FretboardMarker.vue";

export default {
  name: "FretboardDiagram",
  props: {
    instrument: String,
    diagramData: Object
  },
  computed: {
    strings: function() {
      return 6;
    },
    frets: function() {
      return 5;
    },
    markers: function() {
      return this.diagramData.markers.map(function(rawString) {
        const exploded = rawString.split(",");
        return {
          degree: exploded[0],
          string: exploded[1],
          fret: exploded[2]
        };
      });
    },
    label: function() {
      if (this.diagramData.inversion === "root") {
        return "Root Position";
      } else {
        return `${this.diagramData.inversion} Inversion`;
      }
    }
  },
  components: {
    FretboardMarker
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$fretUnit: 25px;
$borderWidth: 3px;

.fretboard-diagram {
  flex-basis: 100%;
}

.fretboard {
  z-index: 10;
  padding: 10px 20px;
}

.string {
  display: flex;
  border-top: $borderWidth solid #111111;
  z-index: 20;
}

.fret {
  flex-grow: 1;
  border-right: $borderWidth solid #111111;
  width: 20px;
  height: $fretUnit;
  z-index: 30;

  &--1 {
    border-left: $borderWidth solid #111111;
  }
}

.fretboard--guitar {
  .string--6 .fret {
    border-left: none;
    border-right: none;
  }
}

/* Larger than phablet */
@media (min-width: 550px) {
  .fretboard-diagram {
    flex-basis: 50%
  }
}

/* Larger than tablet */
@media (min-width: 750px) {
  .fretboard-diagram {
    flex-basis: 33%
  }
}
</style>
