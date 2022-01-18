<template>
  <div id="app">
    <TheMenu :menu="menu" />
    <img :src="menuIcon" class="menu-icon" />
    <TheHeader />
    <p>Du har {{ counter }} todos kvar att göra</p>
    <TodoList :todos="todos" />
    <input type="text" name="" id="" />
    <button>Lägg till todo</button>
  </div>
</template>

<script>
import TheMenu from "./components/TheMenu.vue"
import TheHeader from "./components/TheHeader.vue"
import TodoList from "./components/TodoList.vue"

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
      todos: [
        {
          id: 1,
          content: "Köp mjölk",
          done: false,
        },
        {
          id: 1,
          content: "Köp mjölk",
          done: false,
        },
      ],
      menu: [
        {
          text: "Hide done todos",
          icon: require("./assets/visibility.svg"),
        },
        {
          text: "Delete done todos",
          icon: require("./assets/delete.svg"),
        },
        {
          text: "Clear all data",
          icon: require("./assets/delete_forever.svg"),
        },
      ],
    }
  },
  computed: {},
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
  width: 25rem;
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
</style>
