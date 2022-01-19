<template>
  <div class="list">
    <ul>
      <TodoItem
        v-for="element in todos"
        :key="element.id"
        :todo="element"
        @delete="$emit('delete', element)"
        @check="$emit('check', element)"
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

<style scoped lang="scss">
.list {
  width: 100%;
  margin-top: 1rem;
}
</style>
