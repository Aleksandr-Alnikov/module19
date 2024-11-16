<template>
  <li class="todo__item" :class="{completed: todo.completed}">
    <span @click="$emit('completeTask', todo.id)">{{todo.text}}</span>
    <button @click="$emit('remove', todo.id)">Удалить</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
  .todo__item {
    display: flex;
    justify-content: space-between;
    padding: 8px;
    border-bottom: 1px solid #ccc;
  }

  .completed {
    text-decoration: line-through;
    color: grey;
  }
</style>