<template>
  <div id="app">
    <AddTodo v-on:addTodo="addTodo" />
    <TodosList v-bind:todos="todos" v-on:delTodo="deleteTodo" />
  </div>
</template>

<script>
import TodosList from "./components/Todos";
import AddTodo from "./components/AddTodo";

const todos = [];

export default {
  name: "App",
  components: {
    TodosList,
    AddTodo
  },
  data: () => ({
    todos
  }),
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addTodo(newTodo) {
      this.todos.unshift(newTodo);
    }
  },
  async created() {
    const res = await fetch(
      "http://jsonplaceholder.typicode.com/todos?_limit=10"
    );
    const data = await res.json();
    this.todos = data.map(({ id, title, completed }) => ({
      id,
      title,
      completed
    }));
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
