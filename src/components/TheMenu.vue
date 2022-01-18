<template>
  <div class="menu">
    <div class="fade-layer"></div>
    <img :src="closeIcon" class="close-icon" />
    <nav>
      <div v-for="item in menu" :key="item" class="options">
        <img :src="item.icon" />
        <p>{{ item.text }}</p>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  props: ["menu"],
  data() {
    return {
      closeIcon: require("../assets/close.svg"),
      menuIconShow: true,
    }
  },
  methods: {
    showMenu() {
      this.$emit("click")
    },
  },
}
</script>

<style scoped>
.menu {
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  width: 80%;
  /* background-color: lightblue; */
  display: none;
}

.close-icon {
  align-self: flex-end;
  background-color: lightblue;
}
</style>
