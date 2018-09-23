<template>
  <div :class="['marker', markerClassname]">
  </div>
</template>

<script>
export default {
  name: "FretboardMarker",
  props: {
    stringNum: Number,
    fretNum: Number,
    markerData: Array
  },
  computed: {
    markerClassname: function() {
      for (var i = 0; i < this.markerData.length; i++) {
        if (
          this.markerData[i].string == this.stringNum &&
          this.markerData[i].fret == this.fretNum
        ) {
          return "active marker--" + this.markerData[i].degree;
        }
      }
      return "";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$fretUnit: 30px;
$markerDiameter: 20px;

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
  display: none;

  &.active {
    display: block;
  }

  &--3rd {
    background: #cccccc;
  }

  &--5th {
    background: #000000;
  }
}
</style>
