<template>
  <li class="todo-item">{{ todo.content }}</li>
</template>

<script>
export default {
  props: ["todo"],
}
</script>

<style scoped>
li {
  width: 100%;
  padding: 2rem;
  margin-bottom: 1rem;
  background-color: lightblue;
  list-style: none;
}
</style>
