<template>
  <div class="menu" @click="$emit('close')">
    <img src="../assets/close.svg" class="close-icon" @click="$emit('close')" />
    <nav>
      <div
        v-for="item in menu"
        :key="item.id"
        :menuItem="item"
        class="options"
        @click="$emit('menuFunctions', item)"
      >
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

<style scoped lang="scss">
.menu {
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  position: absolute;
  top: 1rem;
  right: 1rem;
  left: 10%;
  bottom: 40%;
  padding: 1rem;
  background-color: rgb(133, 204, 228);
  border-radius: 5px;
  box-shadow: 0px 0px 27px -18px rgba(0, 0, 0, 0.87);
}

.close-icon {
  align-self: flex-end;
  background-color: rgb(133, 204, 228);
}
nav {
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  .options {
    display: flex;
    margin: 0.8rem;

    img {
      margin-right: 0.5rem;
    }
    a {
      text-decoration: underline;
      cursor: pointer;
    }
  }
}
</style>
