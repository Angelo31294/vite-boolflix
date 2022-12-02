<script>
import { store } from "../store";
import FilmCard from "./FilmCard.vue";
import TvSeriesCard from "./TvSeriesCard.vue";
export default {
  name: "AppMain",
  components: {
    FilmCard,
    TvSeriesCard,
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
    <FilmCard v-for="movie in store.movies" :info="movie" />
    <TvSeriesCard />
  </main>
</template>

<style lang="scss" scoped></style>
