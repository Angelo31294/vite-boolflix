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
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('performSearch')">
      <input
        type="text"
        placeholder="Search..."
        v-model="store.textSearch"
        required
      />
      <button type="submit">Search</button>
    </form>
  </header>
</template>

<style lang="scss" scoped>
header {
  background-color: rgba($color: #000000, $alpha: 0.8);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.875rem 0.625rem;
}
h1 {
  color: red;
  font-size: 3rem;
}
input {
  border: none;
  padding: 0.3125rem;
  border-radius: 0.625rem;
}
button {
  background-color: rgba($color: #fff, $alpha: 0.8);
  border-radius: 0.625rem;
  padding: 0.3125rem;
  margin-left: 0.625rem;
}
</style>
