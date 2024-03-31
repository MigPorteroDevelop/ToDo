<script setup>
import { todos } from '../store/store'

const removeTodo = (index) => {
  todos.value.splice(index, 1);
}
</script>

<template>
  <div class="todo" v-for="(todo, index) in todos" :key="index">
    <p>{{ todo.title }}</p>
    <div>
      <button class="editTodo">&#9998;</button>
      <button type="button" class="removeTodo" @click="removeTodo(index)">&cross;</button>
    </div>
  </div>
</template>

<style scoped>
.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: var(--accent-color);
  margin-top: 30px;
  padding: 0 20px 0 20px;
  border-radius: 10px;
}

.removeTodo {
  border-radius: 50%;
  border: none;
  height: 40px;
  width: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--danger-color);
  cursor: pointer;
}

.editTodo {
  border-radius: 50%;
  border: none;
  height: 40px;
  width: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--accent-color);
}
</style>