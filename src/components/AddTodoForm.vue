<script>
export default {
  data() {
    return {
      todoTitle: "",
    }
  },
  emits: ['submit']
}
</script>

<template>
  <section>
    <form class="addTodoForm">
      <input @input="updateTitle" v-model="todoTitle" type="text" placeholder="ToDo Title">
      <div>
        <button type="button" @click.prevent="~$emit('submit', todoTitle)">Add ToDo</button>
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
