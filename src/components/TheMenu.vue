<template>
  <div>
    <img :src="menuIcon" class="menu-icon" />
    <img :src="closeIcon" class="close-icon" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuIcon: require("../assets/menu.svg"),
      closeIcon: require("../assets/close.svg"),
    }
  },
}
</script>

<style></style>
