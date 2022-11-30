<script>
import FilmCard from "./FilmCard.vue";
import TvSeriesCard from "./TvSeriesCard.vue";
export default {
  name: "AppMain",
  components: {
    FilmCard,
    TvSeriesCard,
  },
};
</script>

<template>
  <main>
    <FilmCard />
    <TvSeriesCard />
  </main>
</template>

<style lang="scss" scoper></style>
