<script>
import CountryFlag from "vue-country-flag-next";
export default {
  name: "FilmCard",
  props: {
    imfo: Object,
  },
  components: {
    CountryFlag,
  },
  methods: {
    getlang(lang) {
      if (lang == "en") {
        return "gb";
      }
      return lang;
    },
  },
  computed: {
    vote() {
      return Math.ceil(this.info.vote_average / 2);
    },
  },
};
</script>

<template>
  <section>
    <h3>{{ info.title }}</h3>
    <h4>{{ info.original_title }}</h4>
    <div>
      <country-flag :country="getFlag(info.original_language)" size="small" />
    </div>
    <div>
      <font-awesome-icon
        v-for="n in 5"
        :icon="n <= vote ? 'fa-star fa-solid' : 'fa-star fa-regular'"
      />
      {{ vote }}
    </div>
  </section>
</template>

<style lang="scss" scoped></style>
