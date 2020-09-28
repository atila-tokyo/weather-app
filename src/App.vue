<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search " />
      </div>

      <div class="weather-wrap">
        <div class="location-box">
          <div class="location">Toshima-ku, JP</div>
          <div class="date">Monday 28 September 2020</div>
        </div>

        <div class="weather-box">
          <div class="temp">27°C</div>
          <div class="weather"></div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => {
    return {};
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
  background-image: url("./assets/seychelles.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
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