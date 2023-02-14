<template>
  <div class="dashboard">
    <div class="dashboard__header">
      <div class="icon__title">
        <h1 class="country__name">{{ weatherData.country }}</h1>
        <font-awesome-icon icon="fa-solid fa-location-dot" size="xl" />
      </div>
    </div>
    <h2>{{ currentTemperature }}</h2>
  </div>
</template>

<script>
import weekdays from '../../weekdays';
export default {
  props: ['country', 'weatherData'],
  computed: {
    currentTemperature() {
      console.log(this.weatherData);
      return this.weatherData.hourly['temperature_2m'][new Date().getHours()] + ' °';
    },
    currentDay() {
      return weekdays[new Date().getDay() - 1];
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
.dashboard {
  padding: 1rem;
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  width: 50vw;
  height: 55vh;
  background-color: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 1rem;
}

.country__name {
  margin: 0;
}

.dashboard__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  margin: 0;
}

.icon__title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.icon__title > h1 {
  margin-right: 0.5rem;
}
</style>
