<template>
  <div class="chord-group">
    <h3>{{ groupData.chordQuality }}</h3>
    <FretboardDiagram
      instrument="guitar"
      v-for="n in groupData.diagrams"
      :key="n.inversion + Date.now()"
      :diagramData="n"
    />
  </div>
</template>

<script>
import FretboardDiagram from "./FretboardDiagram.vue";

export default {
  name: "ChordGroup",
  props: {
    groupData: Object,
  },
  components: {
    FretboardDiagram
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
