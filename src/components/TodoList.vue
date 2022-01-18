<template>
  <div class="list">
    <ul>
      <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" />
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem"
export default {
  components: { TodoItem },
  props: ["todos"],
}
</script>

<style scoped>
.list {
  width: 100%;
}
</style>
