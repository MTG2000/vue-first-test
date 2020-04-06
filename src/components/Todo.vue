<template>
  <div class="todo" v-bind:class="{'isCompleted':todo.completed}">
    <input type="checkbox" v-on:change="toggleTodo" :checked="todo.completed" />
    {{todo.title}}
    <button @click="$emit('delTodo',todo.id)">x</button>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  methods: {
    toggleTodo() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo {
  background: #999;
  padding: 20px 40px;
  color: #fff;
  margin-bottom: 10px;
}

.isCompleted {
  text-decoration: line-through;
}
</style>