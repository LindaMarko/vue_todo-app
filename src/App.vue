<template>
  <div id="app">
    <div
      class="fade-layer"
      :class="{ show: showMenu }"
      @click="closeMenu"
    ></div>
    <img
      src="./assets/menu.svg"
      class="menu-icon"
      @click="showMenu = !showMenu"
      v-if="!showMenu"
    />
    <TheMenu
      :menu="menu"
      v-if="showMenu"
      @close="closeMenu"
      @menuFunctions="hideOrDelete"
    />
    <TheHeader />
    <p>
      Du har <strong>{{ todosLeft }}</strong> todos kvar att göra
    </p>
    <TodoList :todos="visibleTodos" @delete="deleteTodo" @check="checkTodo" />
    <input
      type="text"
      name="new-todo"
      id="new-todo"
      v-model="todoContent"
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

function persist(data) {
  localStorage.setItem("todoData", JSON.stringify(data))
}

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
      todoContent: "",
      showMenu: false,
      showDone: true,
      todos: [],
      menu: [
        {
          id: "hideDone",
          text: "Dölj färdiga todos",
          icon: require("./assets/visibility.svg"),
        },
        {
          id: "deleteDone",
          text: "Radera färdiga todos",
          icon: require("./assets/delete.svg"),
        },
        {
          id: "deleteAll",
          text: "Clear all data",
          icon: require("./assets/delete_forever.svg"),
        },
      ],
    }
  },
  computed: {
    visibleTodos() {
      if (this.showDone) {
        return this.todos
      } else {
        return this.todos.filter((todo) => !todo.done)
      }
    },
    todosLeft() {
      return this.todos.filter((todo) => !todo.done).length
    },
  },
  created() {
    let persistedData = localStorage.getItem("todoData")
    if (persistedData) {
      this.todos = JSON.parse(persistedData)
    }
  },
  methods: {
    closeMenu() {
      this.showMenu = false
    },
    addTodo() {
      this.todos.push({
        id: generateId(),
        content: this.todoContent,
        done: false,
      })
      this.todoContent = ""
      persist(this.todos)
    },
    checkTodo(todo) {
      todo.done = !todo.done
      persist(this.todos)
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((t) => t.id != todo.id)
      persist(this.todos)
    },
    hideOrDelete(menuItem) {
      if (menuItem.id == "hideDone") {
        this.showDone = !this.showDone
      }
      if (menuItem.id == "deleteDone") {
        this.todos = this.todos.filter((t) => !t.done)
      }
      if (menuItem.id === "deleteAll") {
        localStorage.removeItem("todoData")
        this.todos = []
      }
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  overflow: hidden;
  width: 23rem;
  margin: 2rem;
  padding: 1rem;
  box-shadow: 0px 0px 27px -18px rgba(0, 0, 0, 0.87);
}
img {
  cursor: pointer;
}
.menu-icon {
  align-self: flex-end;
}
input,
button {
  width: 100%;
  padding: 0.8rem;
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
.fade-layer {
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.4);
}
.fade-layer {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.4s;
  &.show {
    opacity: 1;
    pointer-events: all;
  }
}
</style>
