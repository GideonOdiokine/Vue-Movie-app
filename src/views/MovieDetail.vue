<template>
  <div class="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <p>{{ movie.Year }}</p>
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <p>{{ movie.Plot }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";

export default defineComponent({
  name: "MovieDetail",
  components: {},
  setup() {
    const movie = ref<{
      Title?: string;
      Year?: string;
      Rated?: string;
      Plot?: string;
      Poster?: string;
    }>({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com?apikey=${process.env.VUE_APP_API_KEY}&i=${route.params.id}&plot=full`
      )
        .then((res) => res.json())
        .then((data) => {
          movie.value = data;
        });
    });

    return {
      movie,
    };
  },
});
</script>

<style lang="scss">
.movie-detail {
  padding: 16px;

  h2 {
    color: #fff;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .featured-img {
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }

  p {
    color: #fff;
    font-size: 18px;
    line-height: 1.4;
  }
}
</style>
