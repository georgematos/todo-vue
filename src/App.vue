<template>
  <div class="" id="app">
    <div class="container grid-xs py-2">
      <img class="img-responsive img-logo" src="@/assets/logo.png" alt="logo do vue">
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input type="text" class="form-input" placeholder="Novo todo" v-model="todo.description">
          <button class='btn btn-primary input-group-btn'>Adicionar</button>
        </div>
      </form>
      <div>
        <ol>
          <li v-for="todo in todos" :key="todo.id">
            {{ todo.id }} - {{ todo.description }} -> {{todo.checked}}
          </li>
        </ol>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      todo: {
        id: 0,
        description: '',
        checked: false
      }
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: Date.now(),
        description: this.todo.description,
        checked: false
      })
    }
  }
}
</script>

<style scoped>
  .img-logo {
    max-width: 200px;
    margin: 0 auto;
  }
</style>
