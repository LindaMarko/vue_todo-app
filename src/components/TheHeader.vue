<template>
  <header>
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
  margin: 1rem 0 4rem 0;
}
h1 {
  text-transform: uppercase;
  font-size: 2.5rem;
}
p {
  font-size: 0.8rem;
}
</style>
