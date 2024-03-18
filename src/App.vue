<script>
import Alert from './components/Alert.vue';

export default {
  components: {
    Alert,
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
    addToDo(e) {
      if (this.todoTitle === "") {
        this.showAlert = true;
        return;
      }

      if (this.todoTitle !== "") {
        this.todos.push(this.todoTitle);
        this.todoTitle = "";
      } else {
        return false
      }
    },
    removeToDo(todo, i) {
      this.todos = this.todos.filter(t => t !== todo);
    }
  }
}

</script>

<template>
  <nav class="navbar">
    <img src="./assets/logo.svg" width="80">
    <div class="brand">ToDo App</div>
  </nav>

  <main class="container">
    <Alert :show="showAlert" @close="showAlert = false" type="warning"/>
    <section>
      <form class="addTodoForm">
        <input @input="updateTitle" v-model="todoTitle" type="text" placeholder="ToDo Title">
        <div>
          <button type="button" @click.prevent="addToDo">Add ToDo</button>
        </div>
      </form>
    </section>

    <section>
      <div v-for="todo in todos" class="todo">
        <p>{{ todo }}</p>
        <div>
          <button class="editTodo">&#9998;</button>
          <button type="button" @click="removeToDo(todo)" class="removeTodo">&cross;</button>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.navbar {
  display: flex;
  align-items: center;
  background: var(--navbar-color);
  padding: 20px;
  margin-bottom: 30px;
}

.brand {
  font-size: 2rem;
}

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
