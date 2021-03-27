<template>
  <div class="List">
    <TestView v-for="(Test, index) in TestList.data" :key="index" v-bind:Test="Test"/>
    <TestEdit />
  </div>
</template>

<script>
import db from "./db";
import TestView from "./TestView";
import TestEdit from "./TestEdit";

export default {
  name: "TestList",
  data() {
    return {
      TestList : []
    };
  },
  async mounted() {
      this.TestList = await db.Get("Test?",[[]]);
  },
  components: {
      TestView,
      TestEdit
  }
};
</script>

<style>
</style>