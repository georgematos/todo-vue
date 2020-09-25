<template>
  <div class="tile flex-centered" :class="{checked: todo.checked}">
    <div class="tile-icon">
      <i class="icon centered" :class="todo.checked ? 'icon-check' : 'icon-time'"></i>
    </div>
    <div class="tile-content">
      <div class="tile-subtitle">{{ todo.description }}</div>
    </div>
    <div class="tile-action">
      <button class="btn btn-link" @click="$emit('toggle')">
        <span v-if="todo.checked">Retomar</span>
        <span v-else>Concluir</span>
      </button>
      <button class="btn btn-link" @click="$emit('remove')">
        <span class="text-error">Remover</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    
  }
}
</script>

<style scoped>
  .checked {
    text-decoration: line-through;
    color: lightgray;
  }
</style>