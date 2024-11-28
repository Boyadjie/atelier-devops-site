<script lang="ts" setup>
import TodoList from "./components/TodoList.vue";
</script>

<template>
  <div id="app">
    <TodoList/>
  </div>
</template>

<style scoped>

#app {
  margin: 0 auto;
  line-height: 1.4;
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #242424;
}
</style>