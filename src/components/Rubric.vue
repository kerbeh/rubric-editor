<template>
  <div>
    This is a Rubric
    <RubricCriterion :criterion="criterion" v-for="criterion in rubric.criteria" :key="criterion.criteria"></RubricCriterion>

    <pre>{{rubric}}</pre>
  </div>
</template>

<script>
import RubricCriterion from "./RubricCriterion.vue";
import RubricStore from "../stores/RubricStore.js";

export default {
  name: "Rubric",
  props: {
    msg: String,
    rubricProp: Object
  },
  data() {
    return {
      rubric: {}
    };
  },
  components: {
    RubricCriterion
  },

  created() {
    /**
     * If no rubric prop has been passed, get the default rubric data from the store
     */
    if (this.rubricProp == undefined) {
      this.rubric = RubricStore.data.rubric;
    } else {
      this.rubric = this.rubricProp;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
