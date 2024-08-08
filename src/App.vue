<script setup>
import Clock from "./components/Clock.vue"
import Timer from "./components/Timer.vue"
import Grade from "./components/Grade.vue"
</script>
<template>
  <Clock/>
  <Timer/>
  <Grade v-for="d in new Array(10)"/>
</template>
<style scoped>
</style>
