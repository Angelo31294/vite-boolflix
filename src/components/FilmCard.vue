<script>
import CountryFlag from "vue-country-flag-next";
export default {
  name: "FilmCard",
  props: {
    info: Object,
  },
  components: {
    CountryFlag,
  },
  methods: {
    getFlag(lang) {
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
  <div class="flip-card" v-if="info.poster_path">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img
          :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
          alt="(info.title, info.name)"
        />
      </div>
      <div class="flip-card-back">
        <h1>{{ info.title }}{{ info.name }}</h1>
        <h2>{{ info.original_title }}{{ info.original_name }}</h2>
        <span>
          <country-flag
            :country="getFlag(info.original_language)"
            size="medium"
          />
        </span>
        <h3>
          <font-awesome-icon
            v-for="n in 5"
            :icon="n <= vote ? 'fa-star fa-solid' : 'fa-star fa-regular'"
          />
          {{ vote }}
        </h3>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.flip-card {
  background-color: transparent;
  width: 21.375rem;
  height: 31.25rem;
  perspective: 62.5rem;
  margin: 1.25rem 0.9375rem;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  text-align: center;
}

img {
  width: 100%;
  height: 100%;
}

h1,
h2,
h3,
span {
  margin-top: 1.25rem;
}
.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  background-color: rgba($color: #000000, $alpha: 0.8);
  color: #fff;
  transform: rotateY(180deg);
}
</style>
