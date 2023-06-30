<template>
  <router-link :to="`/movie/${movie.imdbID}`" class="movie-link">
    <div class="product-image">
      <img :src="movie.Poster" :alt="movie.Title" />
      <h3 class="type">{{ movie.Type }}</h3>
    </div>
    <div class="detail">
      <p class="year">{{ movie.Year }}</p>
      <h3>{{ movie.Title }}</h3>
    </div>
  </router-link>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "MovieCard",
  components: {},
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
});
</script>

<style lang="scss" scoped>
.movie-link {
  display: flex;
  flex-direction: column;
  height: 100%;

  .product-image {
    display: block;
    position: relative;
    img {
      display: block;
      width: 100%;
      height: 275px;
      object-fit: cover;
    }
    .type {
      position: absolute;
      left: 0;
      bottom: 16px;
      padding: 8px 16px;
      background-color: #42b883;
      color: #fff;
      font-size: 16px;
      font-weight: 600;
      text-transform: uppercase;
    }
  }
  .detail {
    background-color: #496583;
    padding: 16px 8px;
    flex: 1 1 100%;
    border-radius: 0px 0px 8px 8px;

    .year {
      color: #aaa;
      font-size: 14px;
    }
    h3 {
      color: #fff;
      font-size: 17px;
      font-family: sans-serif;
    }
  }
}
</style>
