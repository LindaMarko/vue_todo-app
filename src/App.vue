<template>
  <div id="app">
    <TheMenu />
    <TheHeader />
  </div>
</template>

<script>
import TheMenu from "./components/TheMenu.vue"
import TheHeader from "./components/TheHeader.vue"

export default {
  name: "App",
  components: {
    TheHeader,
    TheMenu,
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
  width: 30rem;
  margin: 2rem;
  padding: 1rem;
  box-shadow: 0px 0px 27px -18px rgba(0, 0, 0, 0.87);
}
</style>
