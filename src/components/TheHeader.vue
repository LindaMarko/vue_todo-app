<template>
  <header>
    <TheNav />
    <img :src="logo" alt="logo" />
    <h1>Teflon</h1>
    <p>När det inte fastnar</p>
  </header>
</template>

<script>
export default {
  data() {
    return {
      logo: require("../assets/teflon-panna.svg"),
    }
  },
}
</script>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
h1 {
  text-transform: uppercase;
}
</style>
