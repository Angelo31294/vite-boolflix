<script>
import { store } from "../store";
import FilmCard from "./FilmCard.vue";
export default {
  name: "AppMain",
  components: {
    FilmCard,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <main>
    <FilmCard v-for="movie in store.movie" :info="movie" :show="movie" />
    <FilmCard v-for="serie in store.serie" :info="serie" :show="serie" />
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-wrap: wrap;
  flex-grow: 1;
  padding: 1.25rem;
}
</style>
