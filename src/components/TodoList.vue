<template>
 <div>
   <form @submit.prevent="addTask">
     <input type="text" v-model="newTask" placeholder="Новыя задача" />
     <button type="submit">Добавить</button>
   </form>

    <ul>
      <ToDoItem
          v-for='todo in todos'
          :key='todo.id'
          :todo='todo'
          @remove='removeTask'
          @completeTask='completeTask'
      >
      </ToDoItem>
    </ul>
 </div>
</template>

<script>
import ToDoItem from "@/components/ToDoItem.vue";

export default {
  components: {
    ToDoItem
  },
  data() {
    return {
      newTask: '',
      todos: [],
      nextId: 1,
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.todos.push({
          id:this.nextId++,
          text: this.newTask.trim(),
          completed: false,
        });
        this.newTask = '';
      }
    },
    removeTask(id) {
      this.todos = this.todos.filter(item => item.id !== id);
    },
    completeTask(id) {
      const todo = this.todos.find(item => item.id === id);
      if (todo) {
        todo.completed = !todo.completed;
      }
    },
  }
};
</script>

<style scoped>
  form {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
  }
  button {
    margin-left: 10px;
  }
</style>