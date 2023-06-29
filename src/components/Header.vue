<template>
  <header>
    <router-link to="/">
      <h1><span>Vue</span>Movies</h1>
    </router-link>
  </header>
</template>

<script lang="ts">
export default {};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 16px;
  background-color: #2ced4e;
  box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);

  h1 {
    font-size: 1.5rem;
    color: #fff;
    span {
      color: #42b883;
    }
  }
}
</style>
