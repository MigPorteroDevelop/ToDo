<script setup>
import Alert from './components/Alert.vue';
import Navbar from './components/Navbar.vue';
import AddTodoForm from './components/AddTodoForm.vue';
import TodoItem from './components/TodoItem.vue';
</script>

<template>
  <Navbar />
  <main class="container">
    <Alert />

    <section>
      <!--From AddTodoForm is emited one event with params, to this function-->
      <AddTodoForm @submit="addToDo" />
    </section>
    <section>
      <TodoItem />
    </section>
  </main>
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
