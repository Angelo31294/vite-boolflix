<script>
import { store } from "../store";
export default {
  name: "AppHeader",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <header>
    <form>
      <input type="text" placeholder="Search..." v-model="store.textSearch" />
      <button type="button" @click="$emit('performSearch')">Search</button>
    </form>
  </header>
</template>

<style lang="scss" scoped></style>
