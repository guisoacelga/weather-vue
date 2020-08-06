<template>
  <div id="box">
    <div v-if="loading" id="load">Loading...</div>
    <!-- only shows if loading is true -->
    <div id="weather">
      <h1 id="weatherCity">{{weatherData.cityName}}</h1>
      <div id="weatherDescription">{{weatherData.description}}</div>
      <div id="weatherTemperature">{{weatherData.temperature}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Box",
  props: {
    loading: {       //nombre de la propiedad
      type: Boolean, //qué tipo de elemento espera recibir
    },
    weatherData: {
      type: Object,
    }
  },
};
</script>

<style scoped>
#box {
  text-align: center;
}
#weather {
  padding: 30px;
  border: 1px solid #ccc;
  width: 500px;
  margin: 100px auto auto;
  background-color: deepskyblue;
  box-shadow: 2px 2px 3px #ccc;
  color: white;
  box-sizing: border-box;
  font-weight: bold;
}

#weather h1 {
  font-size: 32px;
  margin-top: 0;
  margin-bottom: 30px;
}

#weatherDescription {
  float: left;
}

#weatherTemperature {
  float: right;
}

#load {
  padding: 30px;
  width: 500px;
  margin: 100px auto auto;
}
</style>