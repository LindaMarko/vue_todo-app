<template>
  <div id="app">
    <img
      :src="menuIcon"
      class="menu-icon"
      @click="showMenu = !showMenu"
      v-if="!showMenu"
    />
    <TheMenu :menu="menu" v-if="showMenu" @close="closeMenu" />
    <TheHeader />
    <p>
      Du har <strong>{{ todosLeft }}</strong> todos kvar att göra
    </p>
    <TodoList :todos="todos" @delete="deleteTodo" />
    <input
      type="text"
      name="new-todo"
      id="new-todo"
      v-model="content"
      @keydown.enter="addTodo"
      placeholder="todo..."
    />
    <button @click="addTodo">Lägg till todo</button>
  </div>
</template>

<script>
import TheMenu from "./components/TheMenu.vue"
import TheHeader from "./components/TheHeader.vue"
import TodoList from "./components/TodoList.vue"

function generateId() {
  return Math.floor(Math.random() * Math.pow(10, 25).toString())
}

export default {
  name: "App",
  components: {
    TheHeader,
    TheMenu,
    TodoList,
  },
  data() {
    return {
      menuIcon: require("./assets/menu.svg"),
      showMenu: false,
      todos: [
        {
          id: 1,
          content: "Köp mjölk",
          done: false,
        },
        {
          id: 2,
          content: "Köp bröd",
          done: false,
        },
      ],
      menu: [
        {
          text: "Dölj färdiga todos",
          icon: require("./assets/visibility.svg"),
        },
        {
          text: "Radera färdiga todos",
          icon: require("./assets/delete.svg"),
        },
        {
          text: "Clear all data",
          icon: require("./assets/delete_forever.svg"),
        },
      ],
    }
  },
  computed: {
    todosLeft() {
      return this.todos.filter((todo) => !todo.done).length
    },
  },
  methods: {
    closeMenu() {
      this.showMenu = false
    },
    addTodo() {
      this.todos.push({
        id: generateId(),
        content: this.content,
        done: false,
      })
      this.content = ""
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((t) => t.id != todo.id)
    },
  },
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Titillium+Web:wght@300;400;700&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Titillium Web", sans-serif;
}
#app {
  position: relative;
  width: 23rem;
  margin: 2rem;
  padding: 1rem;
  box-shadow: 0px 0px 27px -18px rgba(0, 0, 0, 0.87);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.menu-icon {
  align-self: flex-end;
}
input,
button {
  width: 100%;
  padding: 1rem;
}
input {
  margin-top: 1rem;
}
button {
  background-color: black;
  color: white;
  font-family: inherit;
  font-size: 1.2rem;
  font-weight: 700;
  border: none;
}
</style>
