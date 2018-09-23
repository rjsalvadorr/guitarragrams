<template>
  <div :class="['fretboard', 'fretboard--' + instrument]">
    <div v-for="n in strings" :key="n" :class="['string', 'string--' + n]">
      <div v-for="m in frets" :key="m" :class="['fret', 'fret--' + m]">
        <div class='marker'></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FretboardDiagram",
  props: {
    instrument: String,
    strings: Number,
    frets: Number
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$fretUnit: 30px;
$markerDiameter: 20px;

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

.marker {
  background: #ffffff;
  width: $markerDiameter;
  height: $markerDiameter;
  border-radius: 50%;
  margin: auto;
  position: relative;
  top: -$fretUnit / 2;
  border: 4px #000000 solid;
  z-index: 40;
}

.fretboard--guitar {
  .string--6 .fret {
    border-left: none;
    border-right: none;
  }
}
</style>
