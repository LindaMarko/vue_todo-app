<template>
  <li class="todo-item">
    <div>
      <input type="checkbox" />
      <p>{{ todo.content }}</p>
    </div>
    <img
      src="../assets/delete.svg"
      @click="$emit('delete', element)"
      class="delete-icon"
    />
  </li>
</template>

<script>
export default {
  props: ["todo"],
}
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 1.2rem;
  margin-bottom: 0.5rem;
  background-color: lightblue;
  list-style: none;
}
li div {
  display: flex;
  justify-content: flex-start;
}
.delete-icon {
  cursor: pointer;
}
</style>
