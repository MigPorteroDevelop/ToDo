<script>
</script>

<template>
  <nav class="navbar">
    <img src="./assets/logo.svg" width="80">
    <div class="brand">ToDo App</div>
  </nav>

  <main class="container">
    <section>
      <form class="addToDo">
        <input type="text" placeholder="ToDo Title">
        <div>
          <button>Add ToDo</button>
        </div>
      </form>
    </section>

    <section>
      <div class="todo">
        <p>Study</p>
        <div>
          <button class="removeTodo">&times;</button>
          <button></button>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.navbar{
  display: flex;
  align-items: center;
  background: var(--navbar-color);
  padding: 20px;
  margin-bottom: 30px;
}

.brand{
  font-size: 2rem;
}

.addToDo{
  display: flex;
  justify-content: space-between;
}

.addToDo input{
  width: 80%;
  border: solid 2px var(--accent-color);
}

.addToDo button{
  background: var(--accent-color);
  color: var(--text-color);
  border: none;
  height: 50px;
}

.todo{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: var(--accent-color);
  margin-top: 30px;
  padding: 0 20px 0 20px;
  border-radius: 10px;
}

.removeTodo{
  border-radius: 50%;
  border: none;
  height: 40px;
  width: 40px;
  font-size: 30px;
  color: var(--text-color);
  background: var(--danger-color);
}
</style>
