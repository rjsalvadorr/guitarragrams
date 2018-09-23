<template>
  <div class="chord-group">
    <h3 class="chord-group--label">{{ groupData.chordQuality }}</h3>
    <slot></slot>
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
.chord-group {
  &--label {
    text-align: center;
    margin-bottom: 0;
    text-transform: capitalize;
  }

  &--diagrams {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>
