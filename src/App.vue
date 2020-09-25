<template>
  <div class="" id="app">
    <div class="container grid-xs py-2">
      <img
        class="img-responsive img-logo"
        src="@/assets/logo.png"
        alt="logo do vue"
      />
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input
            type="text"
            class="form-input"
            placeholder="Novo todo"
            v-model="todo.description"
            required
          />
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <Todo 
          :todo="t" v-for="t in todos" :key="t.id" 
          @toggle="toggleTodo(t)"
          @remove="removeTodo(t)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Todo from './components/Todo'
export default {
  components: {
    Todo
  },
  data() {
    return {
      todos: [],
      todo: {
        id: 0,
        description: "",
        checked: false,
      },
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: Date.now(),
        description: this.todo.description,
        checked: false,
      });
      this.todo.description = ''
    },
    toggleTodo(t) {
      t.checked = !t.checked
    },
    removeTodo(t) {
      const index = this.todos.indexOf(t);
      // this.todos.splice(index, 1)
      this.$delete(this.todos, index)
    }
  },
};
</script>

<style scoped>
.img-logo {
  max-width: 200px;
  margin: 0 auto;
}
.todo-list {
  padding-top: 2rem;
}
</style>
