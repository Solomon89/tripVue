<template>
  <div class="EditTest" v-if="Test != undefined">
    <input type="text" v-model="Test.name" />
    <input type="text" v-model="Test.description" />
    <input type="check" v-model="Test.isActive" />
    <button @click="Save()">Сохранить</button>
  </div>
</template>

<script>
import db from "./db";

export default {
  name: "TestEdit",
  data() {
    return {
      Test: {},
      Tests: [],
    };
  },
  async mounted() {
    if (this.$route.params.TestId > 0) {
      let response = await db.Get("Test/" + this.$route.params.TestId, [[]]);
      this.Test = response.data;
      
    } else {
      this.Test = {};
      this.Test.name = "";
      this.Test.description = "";
      this.Test.isActive = true;
    }
  },
  methods: {
    Save: async function () {
      let data = "";
      if(this.Test.id > 0)
      {
         data = db.Put("Test",this.Test.id, this.Test);
      }
      else
      {
        data = db.Post("Test?", this.Test);
      }
      
      console.log(data);
    },
  },
};
</script>

<style>
</style>