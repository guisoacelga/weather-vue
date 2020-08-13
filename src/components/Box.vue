<template>
  <div id="box">
    <div v-if="loading" id="load">Loading...</div>
    <div v-if="weatherData.cityName !==''" id="weather">
      <h1 id="weatherCity">{{weatherData.cityName}}</h1>
      <div id="weatherDescription">{{weatherData.description}}</div>
      <div id="weatherTemperature">{{weatherData.temperature}}</div>
      <img id="weatherIcon" :src="'http://openweathermap.org/img/w/' + weatherData.icon + '.png'"/>
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
  padding: 10px;
  border: 1px solid #ccc;
  width: 500px;
  margin: 100px auto auto;
  background-color: deepskyblue;
  box-shadow: 2px 2px 3px #ccc;
  color: white;
  box-sizing: border-box;
  font-weight: bold;
  display: grid;
  grid-template-columns: repeat(3, minmax(100px, 150px));
  grid-template-columns: fitcontent(500px);
  grid-template-rows: 1fr 1fr 1fr;
}

#weather h1 {
  font-size: 32px;
  grid-column: 1 / -1;
}

#weatherDescription {
  grid-column: 1 / 2;
  align-self: end;
}

#weatherIcon {
  grid-column: 1 / 2;
  grid-row: 3 / 4;
  align-self: center;
  justify-self: center;
}

#weatherTemperature {
  grid-column: 3 / 4;
  grid-row: 2 / 3;
  align-self: end;
  justify-self: center;
}

#load {
  padding: 30px;
  width: 500px;
  margin: 100px auto auto;
}
</style>