<template>
  <div id="app" class="container">
    <Header />
    <main>
      <div>
        <Search @startSearchWeather="loading=true" @dataTemp="updateTemp" />
        <Box :loading="loading" :weatherData="weatherData" />
        <!-- props -->
      </div>
    </main>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Search from "./components/Search.vue";
import Box from "./components/Box.vue";

export default {
  name: "App",
  data: () => {
    return {
      loading: false, //by default loading does not appear
      weatherData: {
        cityName: "",
        description: "",
        temperature: "",
      },
    };
  },
  methods: {
    updateTemp(weatherData) {
      this.weatherData = weatherData;
      this.loading = false;
      console.log(weatherData);
    },
  },
  components: {
    Header,
    Search,
    Box,
  },
};
</script>

<style>
.container {
  text-align: center;
}

main {
  padding-top: 80px;
}
</style>
