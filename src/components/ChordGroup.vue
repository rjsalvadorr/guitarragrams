<template>
  <div class="chord-group">
    <h3>{{ groupData.chordQuality }}</h3>
    <div class="chord-group--diagrams">
      <FretboardDiagram
        instrument="guitar"
        v-for="n in groupData.diagrams"
        :key="n.inversion + Date.now()"
        :diagramData="n"
      />
    </div>
  </div>
</template>

<script>
import FretboardDiagram from "./FretboardDiagram.vue";

export default {
  name: "ChordGroup",
  props: {
    groupData: Object
  },
  components: {
    FretboardDiagram
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.chord-group--diagrams {
  display: flex;
}
</style>
