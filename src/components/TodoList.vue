<script lang="ts" setup>
import { ref } from "vue";
import { v4 as uuidv4 } from 'uuid';

import BaseInputText from './BaseInputText.vue'
import TodoListItem from './TodoListItem.vue'

type TodoItem = {
  id: string;
  text: string;
};

const todoList = ref<TodoItem[]>([]);

const addTodo = (inputTextValue: string) => {
  if (inputTextValue) {
    todoList.value.push({ id: uuidv4(), text: inputTextValue });
  }
};

const removeTodo = (idToRemove: string) => {
  const index = todoList.value.findIndex((todoItem) => todoItem.id === idToRemove);
  if (index !== -1) {
    console.log(`Removing todo item with ID ${idToRemove}`);
    todoList.value.splice(index, 1);
  }
};
</script>

<template>
  <div class="card">
    <div class="list">
      <h1>My List for Santa! 🎅</h1>
      <BaseInputText
          @add-todo="addTodo"
      />
      <ul v-if="todoList.length">
        <TodoListItem
            v-for="(todo, index) in todoList"
            :key="index"
            :todo="todo"
            @remove-todo="removeTodo"
        />
      </ul>
      <p v-else>
        Ho! Ho! Ho! What would you like for Christmas ?
      </p>
    </div>
    <img src="/trees.png" alt="christmas trees">
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Mountains+of+Christmas:wght@700&display=swap');

h1 {
  text-align: center;
  font-family: "Mountains of Christmas", serif;
  font-size: 3rem;
}

p {
  text-align: center;
}

.card {
  max-width: 650px;
  background: white;
  box-shadow: 0 0 25px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  overflow: hidden;
  margin: 0 auto;
}

.list {
  width: 70%;
  padding: 20px
}

img {
  max-height: 97vh;
}

ul {
  padding-left: 1rem;
}
</style>
