<template>
  <div class="test">
    <p> {{Test.name}}</p>
    <p> {{Test.description}}</p>
    <p v-if="Test.isActive">
        V
    </p>
   <p v-if="!Test.isActive">
        X
    </p>
  </div>
</template>

<script>

export default {
    name:'TestView',
   props: {
    Test: {}
  }
}
</script>

<style>

</style>