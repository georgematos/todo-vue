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
          />
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <div class="tile flex-centered" v-for="todo in todos" :key="todo.id">
          <div class="tile-icon">
            <i class="icon icon-time centered"></i>
          </div>
          <div class="tile-content">
            <div class="tile-subtitle">{{todo.description}}</div>
          </div>
          <div class="tile-action">
            <button class="btn btn-link">Concluir</button>
            <button class="btn btn-link">
              <span class="text-error">Remover</span>
            </button>
          </div>
        </div>
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
    },
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
