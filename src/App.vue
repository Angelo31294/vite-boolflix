<script>
import axios from "axios";
import { store } from "./store";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getData() {
      axios
        .get("https://api.themoviedb.org/3/movie", {
          params: {
            api_key: "ac8aa3d4c78c853e54f65926f4229842",
            query: this.store.textSearch,
            language: "it-IT",
          },
        })
        .then((resp) => {
          console.log(resp);
        });
    },
  },
};
</script>

<template>
  <AppHeader @performSearch="getData" />
  <AppMain />
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
