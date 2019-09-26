<template>
  <div class="fretboard-diagram">
    <slot></slot>
    <div :class="['fretboard', 'fretboard--' + instrument]">
      <div :class="['fretboard-diagram__label', 'fretboard-diagram__label--' + colorType]">
        <span class="fretboard-diagram__chord-type">{{ diagramLabel }}</span>
        <span class="fretboard-diagram__inversion">{{ inversion }}</span>
      </div>
      <div v-for="n in strings" :key="n" :class="['string', 'string--' + n]">
        <div v-for="m in frets" :key="m" :class="['fret', 'fret--' + m]">
          <FretboardMarker
            :markerData="processedMarkers"
            :stringNum="n"
            :fretNum="m"
            :colorType="colorType"
            :chordType="chordType"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FretboardMarker from "./FretboardMarker.vue";
import { chordLabels, colorTypes } from "../utils/constants";

export default {
  name: "FretboardDiagram",
  props: {
    instrument: String,
    diagramData: Object
  },
  computed: {
    strings: function() {
      // Default to guitar for now.
      return 6;
    },
    fretSize: function() {
      const markers = this.markers;
      let highestFretNum = 0;
      for (var i = 0; i < markers.length; i++) {
        if (markers[i].fret > highestFretNum) {
          highestFretNum = markers[i].fret;
        }
      }
      return highestFretNum;
    },
    frets: function() {
      const defaultFretNum = 4;
      const highestFretNum = this.fretSize;
      let returnFretNum = defaultFretNum;

      if (highestFretNum <= 3) {
        returnFretNum = defaultFretNum;
      } else {
        returnFretNum = highestFretNum;
      }

      return returnFretNum;
    },
    processedMarkers: function() {
      return this.markers.map(function(oldMarker) {
        let processedFret = "";

        if (this.fretSize <= 3) {
          processedFret = oldMarker.fret + 1;
        } else {
          processedFret = oldMarker.fret;
        }

        return {
          degree: oldMarker.degree,
          string: oldMarker.string,
          fret: processedFret
        };
      }, this);
    },
    markers: function() {
      return this.diagramData.markers.map(function(rawString) {
        const exploded = rawString.split(",");
        return {
          degree: exploded[0],
          string: Number(exploded[1]),
          fret: Number(exploded[2])
        };
      });
    },
    inversion: function() {
      if (this.diagramData.inversion === "root") {
        return "root position";
      } else {
        return `${this.diagramData.inversion} inversion`;
      }
    },
    diagramLabel: function() {
      return chordLabels[this.diagramData.chordQuality];
    },
    colorType: function() {
      return colorTypes[this.diagramData.chordQuality];
    },
    chordType: function() {
      return this.diagramData.chordQuality;
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

  &__chord-type,
  &__inversion {
    display: block;
    line-height: 1.1;
  }

  &__chord-type {
    font-weight: bold;
    font-size: 2.5rem;
  }

  &__inversion {
    font-size: 1.75rem;
  }
}

.fretboard-diagram__label {
  text-align: center;
  padding: 0.5rem 0 1.25rem 0;
  border-radius: 6px 6px 0px 0px;
  color: #111111;

  &--maj {
    /* yellow */
    background-color: #fee9b2;
  }

  &--min {
    /* blue */
    background-color: #bbded6;
  }

  &--dim {
    /* red */
    background-color: #ffb6b9;
  }
}

.fretboard {
  z-index: 10;
  padding: 5px 0 0 0;
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

/* Larger than mobile */
@media (min-width: 400px) {
  .fretboard {
    padding: 10px 20px 0 20px;
  }
}

/* Larger than phablet */
@media (min-width: 550px) {
  .fretboard-diagram {
    flex-basis: 50%;
  }
}

/* Larger than desktop */
@media (min-width: 1000px) {
  .fretboard-diagram {
    flex-basis: 33%;
  }
}
</style>
