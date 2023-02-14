<template>
  <form @submit.prevent="searchCountry">
    <input type="text" v-model="countryInput" />
  </form>
</template>

<script>
export default {
  emits: ['search-country'],
  data() {
    return {
      countryInput: '',
    };
  },
  methods: {
    searchCountry() {
      if (this.countryInput.trim().length === 0) return;
      this.$emit('search-country', this.countryInput);
    },
  },
};
</script>

<style scoped>
input {
  width: 20rem;
  height: 4rem;
  background-color: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 1rem;
  font-size: 1.5rem;
  color: #fff;
}
</style>
