<template>
  <div class='fretboard'>
    <div class='string 6'>
      <div class='fret 1'>
        <div class='marker active third'></div>
      </div>
      <div class='fret 2'>
        <div class='marker'></div>
      </div>
      <div class='fret 3'>
        <div class='marker'></div>
      </div>
      <div class='fret 4'>
        <div class='marker'></div>
      </div>
    </div>
    <div class='string 5'>
      <div class='fret 1'>
        <div class='marker'></div>
      </div>
      <div class='fret 2'>
        <div class='marker active root'></div>
      </div>
      <div class='fret 3'>
        <div class='marker'></div>
      </div>
      <div class='fret 4'>
        <div class='marker'></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FretboardDiagram",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.fretboard {
  border: 4px solid #111111;
}
</style>
