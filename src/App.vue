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
    return {
      api_key: "f45eec96406567a2ea35532d84d2dce1",
    };
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

.searchh-box .search-bar {
  display: block;
  width: 100%;
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

.searchh-box .search-bar focus {
  box-shadow: 0ppx, 0px, 16px rgba(0, 0, 0, 0.25);
  background-color: rgb(255, 255, 255, 0.75);
  border-radius: 16px, 0px, 16px, 0px;
}
</style>