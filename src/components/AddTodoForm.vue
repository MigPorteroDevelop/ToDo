<script setup>
</script>

<template>
  <section>
    <form class="addTodoForm">
      <input type="text" placeholder="ToDo Title">
      <div>
        <button type="button">Add ToDo</button>
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
