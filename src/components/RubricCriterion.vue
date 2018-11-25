<template>
  <div>

    <form role="form" class="w-full mb-3 border-grey-light border bg-grey-lightest p-2 rounded ">

      <fieldset class="flex flex-wrap -mx-2 mb-2">
        <div class="w-full lg:w-3/5 px-3 mb-6 md:mb-0">
          <label class="">Level Name
            <input v-model="criterion.name" type="text" class="">
          </label>
          <div class="text-red text-xs italic" v-show="criterion.name">{{titleRemainingChars}} characters remaining.</div>
        </div>

        <div class="w-full lg:w-2/5 px-3 mb-6 md:mb-0">
          <label>Criteria Weight
            <input @input="calculateWeight()" v-model="criterion.weight" type="number">
          </label>
        </div>
      </fieldset>

      <fieldset class="flex">

        <div class="w-1/6">
          <label class="hidden" for="cellLevel1">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level1.edit" class="criterion-cell h-48" id="level1" @click="helloWorld($event)" v-html="criterion.cells.level1.description">
          </div>
          <div v-show="criterion.cells.level1.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level1.description" :options="editorOption"></quill-editor>
            <button id="level1Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level1.value" type="text" readonly>
          </div>
        </div>

        <div class="w-1/6 h-full">
          <label class="hidden" for="cellLevel2">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level2.edit" class="criterion-cell h-48" id="level2" @click="helloWorld($event)" v-html="criterion.cells.level2.description">
          </div>
          <div v-show="criterion.cells.level2.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level2.description" :options="editorOption"></quill-editor>
            <button id="level2Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level2.value" type="text" readonly>
          </div>
        </div>

        <div class="w-1/6">
          <label class="hidden" for="cellLevel3">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level3.edit" class="criterion-cell h-48" id="level3" @click="helloWorld($event)" v-html="criterion.cells.level3.description">
          </div>
          <div v-show="criterion.cells.level3.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level3.description" :options="editorOption"></quill-editor>
            <button id="level3Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level3.value" type="text" readonly>
          </div>
        </div>

        <div class="w-1/6">
          <label class="hidden" for="cellLevel4">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level4.edit" class="criterion-cell h-48" id="level4" @click="helloWorld($event)" v-html="criterion.cells.level4.description">
          </div>
          <div v-show="criterion.cells.level4.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level4.description" :options="editorOption"></quill-editor>
            <button id="level4Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level4.value" type="text" readonly>
          </div>
        </div>

        <div class="w-1/6">
          <label class="hidden" for="cellLevel5">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level5.edit" class="criterion-cell h-48" id="level5" @click="helloWorld($event)" v-html="criterion.cells.level5.description">
          </div>
          <div v-show="criterion.cells.level5.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level5.description" :options="editorOption"></quill-editor>
            <button id="level5Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level5.value" type="text" readonly>
          </div>
        </div>

        <div class="w-1/6">
          <label class="hidden" for="cellLevel6">Criteria 1 "No/poor attempt"</label>
          <div v-show="!criterion.cells.level6.edit" class="criterion-cell h-48" id="level6" @click="helloWorld($event)" v-html="criterion.cells.level6.description">
          </div>
          <div v-show="criterion.cells.level6.edit">
            <quill-editor class="bg-white" v-model="criterion.cells.level6.description" :options="editorOption"></quill-editor>
            <button id="level6Save" type="button" class="btn btn-primary">Save</button>
          </div>

          <div class="w-5/6 mx-auto">
            <label class="hidden" for="criterion-name">Score</label>
            <input class="cursor-not-allowed" v-model="criterion.cells.level6.value" type="text" readonly>
          </div>
        </div>
      </fieldset>

    </form>
  </div>
</template>

<script>
// require styles
import "quill/dist/quill.core.css";
import "quill/dist/quill.snow.css";
import "quill/dist/quill.bubble.css";

import { quillEditor } from "vue-quill-editor";

export default {
  components: {
    // eslint-disable-next-line
    quillEditor
  },
  name: "RubricCriterion",
  props: {
    msg: String,
    criterion: {}
  },
  computed: {
    titleRemainingChars() {
      let remainingChars = 255 - this.criterion.name.length;
      return remainingChars;
    }
  },
  watch: {},
  methods: {
    helloWorld(event) {
      // eslint-disable-next-line
      console.log(event.target.id);
      let cell = event.target.id;
      this.criterion.cells[cell].edit = true;
    },
    calculateWeight() {
      let weight = this.criterion.weight;

      this.criterion.cells.level6.value = weight;
      this.criterion.cells.level5.value = ((weight / 100) * 70).toPrecision(2);
      this.criterion.cells.level4.value = ((weight / 100) * 60).toPrecision(2);
      this.criterion.cells.level3.value = ((weight / 100) * 50).toPrecision(2);
      this.criterion.cells.level2.value = ((weight / 100) * 30).toPrecision(2);
      this.criterion.cells.level1.value = 0;

      var myHeaders = new Headers();
      myHeaders.append("Content-Type", "text/plain");
    }
  },
  data() {
    return {
      editorOption: {
        modules: {
          toolbar: [
            ["bold", "italic", "underline"],
            [{ list: "ordered" }, { list: "bullet" }],
            [{ indent: "-1" }, { indent: "+1" }],
            ["link"],
            [{ color: [] }, { background: [] }]
          ]
        }
      }
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
@import "../../node_modules/bootstrap3/less/bootstrap.less";
</style>

<style scoped>
@import ".././assets/css/tailwind.css";

.criterion-cell {
  @apply border;
  @apply p-2;
  @apply bg-white;
  @apply mx-1;
}

.criterion-cell:hover {
  @apply outline-none;
  @apply shadow-outline;
}

/* Base style for input */
input {
  @apply shadow;
  @apply appearance-none;
  @apply border;
  @apply rounded;
  @apply w-full;
  @apply py-2;
  @apply px-3;
  @apply my-1;
  @apply leading-tight;
}

input:hover {
  @apply outline-none;
  @apply shadow-outline;
}

label {
  @apply text-grey-darker;
  @apply text-sm;
  @apply font-bold;
  @apply mb-2;
}
</style>
