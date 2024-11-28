<script lang="ts" setup>
defineProps<{
  todo: {
    id: string;
    text: string;
  };
}>()

const emit = defineEmits<{
  (e: 'removeTodo', value: string): void;
}>()
</script>

<template>
  <li>
    <span>{{ todo.text }}</span>
    <button name="delete-button" @click="emit('removeTodo', todo.id)"> X </button>
  </li>
</template>

<style scoped>
button {
  background: none;
  color: #d50e0e;
  border: none;
  border-radius: 5px;
  padding: 2px 5px;
  font-size: 1rem;
  font-weight: bold;
  margin-left: 1rem;
}

button:hover {
  cursor: pointer;
  color: #ff0808;
}

li {
  font-family: sans-serif;
  font-size: 1.2rem;
  list-style: none;
  padding: 5px 0;
}

li::before {
  content: '🎁';
  padding-right: 1rem;
}
</style>
