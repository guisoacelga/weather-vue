<template>
  <div id="search"> 
      <!-- v-model: bind the input from the form to the variable --> 
    <input
        v-model="cityName" 
      v-on:keyup.enter="searchWeather()"
      class="form-control form-control-sm col-12 col-lg-6 mt-5"
      type="text"
      id="city"
      placeholder="Type city name"
    />
    <button type="button">Show Weather!</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data: () => {
    return {
      cityName: "", //variable
    };
  },
  methods: {
    searchWeather: function () {
      this.$emit("startSearchWeather"); //emit event --> goes to parent; debe ser string (nombre evento)
        if (this.cityName.trim().length === 0) {
        return alert("Please enter a City Name");
      }
      var http = new XMLHttpRequest();
      var apiKey = "INSERT HERE API KEY";
      var url =
        "http://api.openweathermap.org/data/2.5/weather?q=" +
        this.cityName +
        "&units=metric&appid=" +
        apiKey;
      const method = "GET";

      http.open(method, url);
      http.onreadystatechange = () => {
        if (http.readyState == XMLHttpRequest.DONE && http.status === 200) {
          const data = JSON.parse(http.responseText);
          const weatherData = {
              cityName: this.cityName,
              description: data.weather[0].description.toUpperCase(),
              temperature: data.main.temp
          }
            this.$emit("dataTemp", weatherData); //nombre del evento, datos transmitidos
         
        } else if (http.readyState === XMLHttpRequest.DONE) {
          alert("Something went wrong!");
        }
      };
      http.send(); 
    },
  },
};
</script>

<style scoped>
#search {
  font-size: 18px;
  text-align: center;
}

#search input {
  font-size: inherit;
  font-family: inherit;
  margin: auto;
}

#search button {
  font-family: inherit;
  font-size: inherit;
  background-color: dodgerblue;
  border: 1px solid dodgerblue;
  border-radius: 3px;
  cursor: pointer;
  color: white;
  margin-top: 20px;
}

#search button:hover {
  background-color: deepskyblue;
}
</style>