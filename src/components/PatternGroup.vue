<template>
  <div class="pattern-group" :id="customId">
    <h2 class="pattern-group__label">{{ groupData.patternType }}</h2>
    <slot></slot>
    <div class="pattern-group__diagrams">
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
    groupData: Object,
    customId: String
  },
  components: {
    FretboardDiagram
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pattern-group {
  margin-bottom: 5rem;

  & > p {
    text-align: center;
    padding: 0 0 10px 0;
    margin-bottom: 0.5rem;
  }

  &__label {
    text-align: center;
    padding: 0;
    margin-bottom: 0.5rem;
  }

  &__diagrams {
    display: flex;
    flex-wrap: wrap;
  }
}

/* Larger than mobile */
@media (min-width: 400px) {
  .pattern-group {
    & > p {
      text-align: left;
      padding: 0 20px 10px 20px;
    }

    &__label {
      text-align: left;
      padding: 0 20px;
    }
  }
}
</style>
