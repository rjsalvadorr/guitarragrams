<template>
  <div :class="['marker', markerClassname]">
    <div class="marker-tag">{{ markerTag }}</div>
  </div>
</template>

<script>
import { markerTags } from "../utils/constants";

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
    },
    markerTag: function() {
      for (var i = 0; i < this.markerData.length; i++) {
        if (
          this.markerData[i].string == this.stringNum &&
          this.markerData[i].fret == this.fretNum
        ) {
          return markerTags[this.markerData[i].degree];
        }
      }
      return "";
    }
  }
};
</script>

<!-- Not scoped, so the CSS is shared with other components -->
<style lang="scss">
$fretUnit: 25px;
$markerDiameter: $fretUnit * 0.75;
$borderWidth: 3px;

.marker {
  background: #ffffff;
  width: $markerDiameter;
  height: $markerDiameter;
  border-radius: 50%;
  margin: auto;
  position: relative;
  top: -$fretUnit / 1.75;
  border: $borderWidth #000000 solid;
  z-index: 40;
  display: none;

  .marker-tag {
    font-weight: bold;
    font-size: $fretUnit / 1.8;
    line-height: $fretUnit / 1.8;
    margin-top: $fretUnit / 12;
  }

  &.active {
    display: block;
  }

  &--root {
    background: #ffffff;

    .marker-tag {
      color: #000000;
    }
  }

  &--3rd {
    background: #aaaaaa;

    .marker-tag {
      color: #000000;
    }
  }

  &--5th {
    background: #000000;

    .marker-tag {
      color: #ffffff;
    }
  }

  &--7th {
    background: #888888;

    .marker-tag {
      color: #000000;
    }
  }

  &--9th {
    background: #ffffff;

    .marker-tag {
      color: #000000;
    }
  }
}
</style>
