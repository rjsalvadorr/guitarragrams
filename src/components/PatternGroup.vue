<template>
  <div class="pattern-group">
    <h2 class="pattern-group--label">{{ groupData.patternType }}</h2>
    <slot></slot>
    <div class="pattern-group--diagrams">
      <FretboardDiagram
        instrument="guitar"
        v-for="n in groupData.diagrams"
        :key="n.chordQuality + n.inversion + Date.now()"
        :diagramData="n"
      />
    </div>
  </div>
</template>

<script>
import FretboardDiagram from "./FretboardDiagram.vue";

export default {
  name: "PatternGroup",
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
.pattern-group {
  margin-bottom: 7rem;

  & > p {
    text-align: left;
    padding-left: 20px;
    margin-bottom: 0.5rem;
  }

  &--label {
    text-align: left;
    padding-left: 20px;
    margin-bottom: 0.5rem;
  }

  &--diagrams {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>
