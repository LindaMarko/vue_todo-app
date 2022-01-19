<template>
  <li class="todo-item" :class="{ done: todo.done }">
    <input type="checkbox" class="checkbox" @input="$emit('check', element)" />
    {{ todo.content }}
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

<style scoped lang="scss">
.todo-item {
  display: flex;

  align-items: center;
  // width: 100%;
  padding: 1.2rem;
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
  img {
    align-self: flex-end;
  }
}
</style>
