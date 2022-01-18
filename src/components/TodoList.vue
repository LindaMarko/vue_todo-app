<template>
  <div class="list">
    <ul>
      <TodoItem
        v-for="element in todos"
        :key="element.id"
        :todo="element"
        @delete="$emit('delete', element)"
      />
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
  margin-top: 1rem;
}
</style>
