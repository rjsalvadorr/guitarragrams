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
    markerData: Array,
    colorType: String,
  },
  computed: {
    markerClassname: function() {
      let className = '';
      for (var i = 0; i < this.markerData.length; i++) {
        if (
          this.markerData[i].string == this.stringNum &&
          this.markerData[i].fret == this.fretNum
        ) {
          className = `active marker--${this.markerData[i].degree}`;
          className += ` marker--${this.colorType}`;
          return className;
        }
      }
      return "";
    },
    markerTag: function() {
      console.log(this.stringNum, this.fretNum, this.markerData, this.colorType);
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

  &-tag {
    font-weight: bold;
    font-size: $fretUnit / 1.8;
    line-height: $fretUnit / 1.8;
    margin-top: $fretUnit / 12;
  }

  &.active {
    display: block;
  }
}

.marker--root {
  background: #ffffff;

  .marker-tag {
    color: #000000;
  }
}

.marker--3rd {
  background: #aaaaaa;

  &.marker--maj {
    background-color: scale-color(#fee9b2, $lightness: -20%, $saturation: -5%);
  }

  &.marker--min {
    background-color: scale-color(#bbded6, $lightness: -20%, $saturation: -5%);
  }
  
  &.marker--dim {
    background-color: scale-color(#ffb6b9, $lightness: -20%, $saturation: -5%);
  }

  .marker-tag {
    color: #000000;
  }
}

.marker--5th {
  background: #000000;

  &.marker--dim {
    background-color: #660000;
  }

  .marker-tag {
    color: #ffffff;
  }
}

.marker--7th {
  background: #888888;

  &.marker--maj {
    background-color: #fee9b2;
  }

  &.marker--min {
    background-color: #bbded6;
  }
  
  &.marker--dim {
    background-color: #ffb6b9;
  }

  .marker-tag {
    color: #000000;
  }
}

.marker--9th {
  background: #cccccc;

  .marker-tag {
    color: #000000;
  }
}
</style>
