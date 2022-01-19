<template>
  <li class="todo-item" :class="{ done: todo.done }">
    <span
      ><input
        type="checkbox"
        class="checkbox"
        :checked="todo.done"
        @input="$emit('check', element)"
      />
      <p>{{ todo.content }}</p></span
    >
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
  data() {
    return { element: {} }
  },
}
</script>

<style scoped lang="scss">
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  margin-bottom: 0.5rem;
  background-color: lightblue;
  list-style: none;

  &.done {
    text-decoration: line-through;
    color: rgb(32, 118, 158);
  }

  div {
    display: flex;
    align-items: center;
  }

  .checkbox {
    margin: 0;
    margin-right: 0.5rem;
    border-radius: 50%;
    width: 15px;
    height: 15px;
  }
  span {
    display: flex;
    align-items: center;
  }
}
</style>
