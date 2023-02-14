<template>
  <div>
    <h1>{{ weatherData.country }}</h1>
    <h2>{{ weatherData.hourly }}</h2>
  </div>
</template>

<script>
export default {
  props: ['country', 'weatherData'],
};
</script>

<style scoped>
div {
  font-family: sans-serif;
  width: 50vw;
  height: 55vh;
  background-color: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 1rem;
}
</style>
