<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img
          src="https://media.istockphoto.com/id/638250692/photo/young-woman-with-friends-watching-movie.jpg?s=2048x2048&w=is&k=20&c=ZfXYasao1FcZt5AEYl58JnuoXXJvkAeaqCYO4TxEIO0="
          alt="The Dark Knight"
          class="feature-img"
        />
        <div class="detail">
          <h3>Naruto</h3>
          <p>
            Naruto is an anime series based on Masashi Kishimoto's manga series
            and published by Shueisha. It is the story of Naruto Uzumaki, a
            young ninja who seeks to gain recognition from his peers.
          </p>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeView",
  components: {},
});
</script>

<style lang="scss" scoped>
.home {
  .feature-card {
    position: relative;

    .feature-img {
      display: block;
      width: 100%;
      height: 300px;
      object-fit: cover;
      position: relative;
      z-index: 0;
    }
    .detail {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;

      h3 {
        color: #fff;
        margin-bottom: 16px;
      }
      p {
        color: #fff;
      }
    }
  }
}
</style>
