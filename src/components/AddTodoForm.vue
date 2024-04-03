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
  color: #FFF;
  height: 50px;
  border: 2px solid var(--text-color);
  border-radius: 10px;
  padding: 18px 36px;
  display: inline-block;
  font-family: "Lucida Console", Monaco, monospace;
  font-size: 14px;
  letter-spacing: 1px;
  box-shadow: inset 0 0 0 0 #ffffff;
  -webkit-transition: ease-out 0.4s;
  -moz-transition: ease-out 0.4s;
  transition: ease-out 0.4s;
  cursor: pointer;
}

.addTodoForm button:hover {
  box-shadow: inset 0 0 0 50px #ffffff;
  color: var(--accent-color);
  border: 2px solid var(--accent-color);
}
</style>
