<script>
import axios from "axios";
import { store } from "./store";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppError from "./components/AppError.vue";
export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
    AppError,
  },
  data() {
    return {
      store,
      error: false,
    };
  },
  methods: {
    getData() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "ac8aa3d4c78c853e54f65926f4229842",
            query: this.store.textSearch,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.store.movie = resp.data.results;
          if (this.error) {
            this.error = !this.error;
          }
        })
        .catch((err) => {
          this.error = true;
        });
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "ac8aa3d4c78c853e54f65926f4229842",
            query: this.store.textSearch,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.store.serie = resp.data.results;
          if (this.error) {
            this.error = !this.error;
          }
        })
        .catch((err) => {
          this.error = true;
        });
    },
  },
};
</script>

<template>
  <AppHeader @performSearch="getData" />
  <AppError v-if="error" />
  <AppMain />
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
