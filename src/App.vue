<template>
  <div id="app">
    <h1>Список дел</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList.vue";

export default {
  name: 'App',
  components: {
    TodoList
  },
};
</script>

<style>
  #app {
    max-width: 600px;
    margin: 50px auto;
  }
</style>
