<template>
  <div id="app" v-bind:class="[background]">
    <main>
      <div class="search-box">
        <input
          type="text"
          class="search-bar"
          placeholder="Search "
          v-model="query"
          @keypress="fetchMaker"
        />
      </div>

      <div class="weather-wrap" v-if="typeof result.main != undefined">
        <div class="location-box">
          <div class="location">
            {{ result.name }}, {{ result.sys.country }}
          </div>
          <div class="date">{{ givenDate() }}</div>
        </div>

        <div class="weather-box">
          <div class="temp">{{ `${Math.round(result.main.temp)} °C` }}</div>
          <div class="weather">{{ result.weather[0].description }}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      query: "",
      url: process.env.VUE_APP_BASE_URL,
      api_key: process.env.VUE_APP_API_KEY,
      result: {
      name:"",
      sys:{country:""},
      weather: [{description:""}],
      main:{temp:""}
      },
      background: "clear sky",
    }
  },
  methods: {
    fetchMaker (element) {
      if (element.key == "Enter") {
        console.log(process.env.VUE_APP_BASE_URL);
        fetch(
          `${this.url}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.givenResult);
      }
    },
    givenResult (result) {
      this.result = result;
      console.log(this.getBackground());
      this.background = this.getBackground();
      
    },
    givenDate () {
      let el = new Date();
      const months = [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jul",
        "Jun",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec",
      ];

      const weekDay = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];

      let day = weekDay[el.getDay()];
      let date = el.getDate();
      let month = months[el.getMonth()];
      let year = el.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
    getBackground () {

      if (
        this.result.main != "undefined" &&
        this.result.weather[0].main == "Clear"
      ) {
        return "warm";
      } else if (
        (typeof this.result.main != "undefined" &&
          this.result.weather[0].main == "shower rain" ||
        this.result.weather[0].main == "light rain")
      ) {
        return "shower-rain";
      } else if (
        typeof this.result.main != "undefined" &&
        this.result.weather[0].main == "rain"
      ) {
        return "rain";
      } else {
        return "";
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "fantasy", sans-serif;
}

#app {
  background-image: url("./assets/winter-mountain.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url("./assets/seychelles.jpg");
}

#app.rain {
  background-image: url("./assets/rain.jpg");
}

#app.shower-rain {
  background-image: url("./assets/rain.jpg");
}

main {
  min-height: 100vh;
  padding: 30px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25));
}

.search-box {
  margin-bottom: 30px;
}
.search-box .search-bar {
  display: block;
  width: 30%;
  padding: 15px;
  color: #404040;
  font-size: 25px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0ppx, 0px, 8px rgba(0, 0, 0, 0.25);
  background-color: rgb(255, 255, 255, 0.5);
  border-radius: 0px, 16px, 0px, 16px;
  transition: 0.6s;
}

.search-box .search-bar focus {
  box-shadow: 0ppx, 0px, 16px rgba(0, 0, 0, 0.25);
  background-color: rgb(255, 255, 255, 0.75);
  border-radius: 16px, 0px, 16px, 0px;
}

.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px, 3px rgba(0, 0, 0, 0.25);
}

.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px, 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #fff;
  font-size: 20px;
  font-weight: 300px;
  font-style: italic;
  text-align: center;
}

weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 8px 20px;
  color: #fff;
  font-size: 80px;
  font-weight: 1000;

  text-shadow: 4px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 20px;
  margin: 35px 0px;

  box-shadow: 4px 8px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #ffff;
  font-size: 50px;
  font-weight: 800;
  font-style: italic;
  text-shadow: 4px 6px rgba(255, 255, 255, 0.25);
}
</style>
