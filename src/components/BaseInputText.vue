<script lang="ts" setup>
import { ref } from "vue";

const emit = defineEmits<{
  (e: 'add-Todo', value: string): void;
}>();

const todoText = ref<string>('');

const addTodo = () => {
  emit("add-Todo", todoText.value)
  todoText.value = '';
}

</script>

<template>
  <input
    type="text"
    class="input"
    placeholder="Ex: A full day TechnoZaure..."
    v-model="todoText"
    @keydown.enter="addTodo"
  />
</template>

<style scoped>
input {
  display: block;
  width: 380px;
  margin: 0 auto;
  font-size: 1rem;
  padding: 5px 10px;
}
</style>
