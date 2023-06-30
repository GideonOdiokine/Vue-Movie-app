<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img
          src="https://images.pexels.com/photos/3131971/pexels-photo-3131971.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
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
    <form @submit.prevent="SearchMovies()" class="search-box">
      <input
        type="text"
        v-model="searchQuery"
        placeholder="What are you looking for?"
      />
      <input type="submit" value="Search" />
    </form>

    <div class="movies-list">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <MovieCard :movie="movie" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import MovieCard from "../components/MovieCard.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    MovieCard,
  },
  setup() {
    const searchQuery = ref("");
    const movies = ref([]) as any;

    const SearchMovies = () => {
      if (searchQuery.value != "") {
        fetch(
          `http://www.omdbapi.com?apikey=${process.env.VUE_APP_API_KEY}&s=${searchQuery.value}`
        )
          .then((res) => res.json())
          .then((data) => {
            movies.value = data.Search;
            searchQuery.value = "";
          });
      }
    };

    return {
      searchQuery,
      movies,
      SearchMovies,
    };
  },
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
  .search-box {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 16px;
    flex-direction: column;

    input {
      display: block;
      appearance: none;
      border: none;
      background: none;
      outline: none;

      &[type="text"] {
        padding: 10px 16px;
        width: 100%;
        color: #fff;
        font-size: 20px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;

        &::placeholder {
          color: #f3f3f3;
        }
        &:focus {
          box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
        }
      }
      &[type="submit"] {
        width: 100%;
        max-width: 300px;
        padding: 16px;
        color: #fff;
        font-size: 20px;
        border-radius: 8px;
        background-color: #42b883;
        text-transform: uppercase;
        transition: 0.4s;

        &:active {
          background-color: #3b8070;
        }
      }
    }
  }
  .movies-list {
    display: flex;
    flex-wrap: wrap;
    margin: 0px 8px;

    .movie {
      max-width: 50%;
      flex: 1 1 50%;
      padding: 16px 8px;

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
    }
  }
}
</style>
