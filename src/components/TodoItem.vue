<script setup>
import { todos } from '../store/store'

const editTodo = (index, title) => {
  //Añado una propiedad "editing", para rastrear que se está modificando
  todos.value[index].editing = true;
  //Al entrar en modo "editing", le podemos asignar un nuevo título temporalmente.
  todos.value[index].newTitle = title;
};

const applyEdit = (index) => {
  // Actualiza el título
  todos.value[index].title = todos.value[index].newTitle; 
  // Sale del modo edición
  todos.value[index].editing = false; 
};

const removeTodo = (index) => {
  todos.value.splice(index, 1);
}
</script>

<template>
  <div class="todo" v-for="(todo, index) in todos" :key="index">
    <p v-if="!todo.editing">{{ todo.title }}</p>
    <input v-else v-model="todo.newTitle" type="text"></input>
    <div>
      <button type="button" class="editTodo" @click="editTodo(index)">&#9998;</button>
      <button type="button" class="applyEdit" v-if="todo.editing" @click="applyEdit(index)">&#x2713;</button>
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
  border-radius: 100%;
  border-color: white;
  height: 40px;
  width: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--accent-color);
  cursor: pointer;
}

.applyEdit {
  border-radius: 100%;
  border-color: white;
  height: 40px;
  width: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--accent-color);
  cursor: pointer;
}
</style>