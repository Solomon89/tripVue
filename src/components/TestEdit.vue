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
            Test: {}
      }
    
  },
   mounted() {
       this.Test = {};
       this.Test.name = '';
       this.Test.description = '';
       this.Test.isActive = true;

   },
   methods: {
                Save:async function() {
                    const data = db.Post("Test?",this.Test)
                console.log(data);
                }
            }
};
</script>

<style>
</style>