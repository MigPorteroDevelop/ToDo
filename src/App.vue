<script>
import Alert from './components/Alert.vue';
import Navbar from './components/Navbar.vue';
import AddTodoForm from './components/AddTodoForm.vue';

export default {
  components: {
    Alert,
    Navbar,
    AddTodoForm
  },
  data() {
    return {
      todoTitle: "",
      todos: [],
      showAlert: false
    }
  },

  methods: {
    updateTitle(e) {
      this.todoTitle = e.target.value
    },
    addToDo(title) {
      if (title === "") {
        this.showAlert = true;
        return;
      }

      if (title !== "") {
        const todoItem = {
          id: Math.floor(Math.random() * 1000),
          title: title
        };
        this.todos.push(todoItem);
        this.todoTitle = "";
      } else {
        return false
      }
    },
    removeToDo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    }
  }
}

</script>

<template>
  <Navbar />
  <main class="container">
    <Alert :show="showAlert" @close="showAlert = false" type="warning" />
    <section>
      <!--From AddTodoForm is emited one event with params, to this function-->
      <AddTodoForm @submit="addToDo" />
    </section>
    <section>
      <div v-for="todo in todos" :key="todo.id" class="todo">
        <p>{{ todo.title }}</p>
        <div>
          <button class="editTodo">&#9998;</button>
          <button type="button" @click="removeToDo(todo.id)" class="removeTodo">&cross;</button>
        </div>
      </div>
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
