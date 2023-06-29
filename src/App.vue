<template>
  <div>
    <Header />
    <main>
      <router-view />
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Header from "./components/Header.vue";

export default defineComponent({
  name: "App",
  components: {
    Header,
  },
});
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;

  &::selection {
    background-color: transparentize(#428883, 0.5);
  }
  body {
    background-color: #35495e;
  }
  a {
    text-decoration: none;
    /* color: #fff; */
  }
}
</style>
