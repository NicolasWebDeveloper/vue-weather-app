<template>
  <base-spinner v-if="isLoading"></base-spinner>
  <app-search v-if="showSearch" @search-country="searchCountry"></app-search>
  <app-container v-else :weatherData="weatherData"></app-container>
</template>

<script>
import AppContainer from './components/ui/AppContainer.vue';
import AppSearch from './components/ui/AppSearch.vue';
import BaseSpinner from './components/base/BaseSpinner.vue';

export default {
  components: { AppContainer, AppSearch, BaseSpinner },
  data() {
    return {
      showSearch: true,
      weatherData: {
        country: '',
        hours: [],
      },
      isLoading: false,
    };
  },
  methods: {
    async searchCountry(country) {
      try {
        this.isLoading = true;

        const geoRes = await fetch(`https://geocoding-api.open-meteo.com/v1/search?name=${country}`);
        if (!geoRes.ok) throw new Error('Error while fetching country information');

        const geoData = await geoRes.json();
        const results = geoData.results;

        if (!results || results.length === 0) throw new Error('Invalid country!');

        const { longitude, latitude } = results[0];
        const weatherRes = await fetch(
          `https://api.open-meteo.com/v1/forecast?latitude=${latitude}&longitude=${longitude}&hourly=temperature_2m`
        );
        this.weatherData = await weatherRes.json();
        this.weatherData.country = results[0].country;
        this.weatherData.hours = weatherRes.data;
        this.showSearch = false;
      } catch (err) {
        this.showSearch = true;
        console.error(err);
      } finally {
        this.isLoading = false;
      }
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  background-image: linear-gradient(90deg, #784bff, #b144cc);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
}
</style>
