<template>
  <div class='fretboard'>
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
    strings: Number,
    frets: Number
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.fretboard {
  border: 4px solid #111111;
}
</style>
