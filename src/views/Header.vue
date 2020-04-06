<template>
  <header id="header" class="header">
    <h1>Todo App</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss" scoped>
header {
  background-color: black;
  color: white;
}
</style>
