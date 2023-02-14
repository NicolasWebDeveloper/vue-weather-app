<template>
  <app-container></app-container>
</template>

<script>
import AppContainer from './components/AppContainer.vue';

export default {
  components: { AppContainer },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  background-color: #0a0c0d;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
}
</style>
