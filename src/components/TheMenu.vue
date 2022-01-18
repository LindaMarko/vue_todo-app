<template>
  <div class="menu">
    <div class="fade-layer"></div>
    <img :src="closeIcon" class="close-icon" @click="$emit('close')" />
    <nav>
      <div v-for="item in menu" :key="item" class="options">
        <img :src="item.icon" />
        <a>{{ item.text }}</a>
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
  position: absolute;
  top: 0;
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  width: 90%;
  background-color: lightblue;
}

.close-icon {
  align-self: flex-end;
  background-color: lightblue;
}
.options {
  display: flex;
}
</style>
