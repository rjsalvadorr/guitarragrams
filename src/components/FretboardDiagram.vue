<template>
  <div class="fretboard-diagram-container">
    <span>{{ diagramData.inversion }}</span>
    <div :class="['fretboard', 'fretboard--' + instrument]">
      <div v-for="n in strings" :key="n" :class="['string', 'string--' + n]">
        <div v-for="m in frets" :key="m" :class="['fret', 'fret--' + m]">
          <FretboardMarker :markerData="markers" :stringNum="n" :fretNum="m"/>
        </div>
      </div>
      <h4>Debug info (FretboardDiagram)</h4>
      <pre>
        <code>{{ `diagramData = ${JSON.stringify(diagramData, null, 2)}` }}</code>
        <code>{{ `strings = ${JSON.stringify(strings, null, 2)}` }}</code>
        <code>{{ `frets = ${JSON.stringify(frets, null, 2)}` }}</code>
        <code>{{ `markers = ${JSON.stringify(markers, null, 2)}` }}</code>
      </pre>
    </div>
  </div>
</template>

<script>
import FretboardMarker from './FretboardMarker.vue';

export default {
  name: "FretboardDiagram",
  props: {
    instrument: String,
    diagramData: Object,
  },
  computed: {
    strings: function () {
      return 6;
    },
    frets: function () {
      return 5;
    },
    markers: function() {
      return this.diagramData.markers.map(function(rawString) {
        const exploded = rawString.split(',');
        return {
          degree: exploded[0],
          string: exploded[1],
          fret: exploded[2]
        }
      });
    }
  },
  components: {
    FretboardMarker
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$fretUnit: 30px;

.fretboard {
  z-index: 10;
}

.string {
  display: flex;
  border-top: 4px solid #111111;
  z-index: 20;
}

.fret {
  flex-grow: 1;
  border-right: 4px solid #111111;
  width: 20px;
  height: $fretUnit;
  z-index: 30;

  &--1 {
    border-left: 4px solid #111111;
  }
}

.fretboard--guitar {
  .string--6 .fret {
    border-left: none;
    border-right: none;
  }
}
</style>
