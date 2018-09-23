<template>
  <div class="pattern-group">
    <h2 class="pattern-group--label">{{ groupData.patternType }}</h2>
    <slot></slot>
    <ChordGroup v-for="n in groupData.chordGroups" :key="n.chordQuality + Date.now()" :groupData="n" />
  </div>
</template>

<script>
import ChordGroup from "./ChordGroup.vue";

export default {
  name: "PatternGroup",
  props: {
    groupData: Object
  },
  components: {
    ChordGroup
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pattern-group {
  margin-bottom: 4rem;

  &--label {
    text-align: center;
    margin-bottom: 1rem;
  }

  p {
    text-align: center;
  }
}
</style>
