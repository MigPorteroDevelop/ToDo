<script setup>
import { todos } from '../store/store'
import { ref } from 'vue';
import Alert from './Alert.vue';

const todoTitle = ref("");
const showAlert = ref(false);

const uniqueId = () => {
  return Math.random().toString(36).substr(2, 9);
};

const addToDoTitle = () => {
  const newTodo = {
    id: uniqueId(),
    title: todoTitle.value
  }
  if (todoTitle.value !== "") {
    todos.value.push(newTodo);
    todoTitle.value = "";
    //Resetea el estado
    showAlert.value = false;
  } else {
    showAlert.value = true;
  }
}
</script>

<template>
  <section>
    <Alert v-if="showAlert" />
    <form class="addTodoForm">
      <input type="text" v-model="todoTitle" placeholder="ToDo Title">
      <div>
        <button type="button" @click="addToDoTitle">Add ToDo</button>
      </div>
    </form>
  </section>
</template>

<style scoped>
.addTodoForm {
  display: flex;
  justify-content: space-between;
}

.addTodoForm input {
  width: 80%;
  border: solid 2px var(--accent-color);
}

.addTodoForm button {
  background: var(--accent-color);
  color: var(--text-color);
  border: none;
  height: 50px;
}
</style>
