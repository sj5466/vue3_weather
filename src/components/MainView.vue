<template>
  <div class="leftContainer">
    <div id="cityNameBox">
      <div class="cityName">
        <p>{{ cityName }}</p>
        <p>{{ currentTime }}</p>
      </div>
    </div>
    <div id="contentsBox">
      <div class="buttonBox">
        <div class="buttonBackground">
          <button class="forecast">Forecast</button>
          <button class="airquality">Air Quality</button>
        </div>
      </div>
      <div class="weatherBox">
        <div class="weatherDegree">
          <p>{{ currentTemp }}&deg;</p>
        </div>
        <div class="weatherIcon">
          <img :src="images[0]" alt="MainLogo" />
        </div>
        <div class="weatherData">
          <div
            v-for="temporary in temporaryData"
            :key="temporary.title"
            class="detailData"
          >
            <p>{{ temporary.title }}</p>
            <p>{{ temporary.value }}</p>
          </div>
        </div>
      </div>
    </div>
    <div id="todayWeather">
      <div class="textBox">
        <p>시간대별 날씨 정보</p>
        <p>이번주 날씨 보기</p>
      </div>
      <div class="timelyWeatherBox">
        <div
          class="timelyWeather"
          v-for="(temp, index) in arrayTemps"
          :key="index"
        >
          <div class="icon">
            <img :src="images[index]" alt="이미지" />
          </div>
          <div class="data">
            <p class="time">
              {{ Unix_timestamp(temp.dt) }}
            </p>
            <p class="currentDegree">{{ Math.round(temp.temp) }}&deg;</p>
            <div>
              <img src="~/assets/images/drop.png" alt="이미지" />
              <p class="fall">{{ temp.humidity }}%</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav>
      <i class="fas fa-home"></i>
      <i class="fas fa-search-location"></i>
      <i class="fas fa-chart-line"></i>
      <i class="fas fa-cog"></i>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      temporaryData: [
        { title: "습도", value: "89%" },
        { title: "풍속", value: "10m/s" },
        { title: "풍향", value: "WS" },
      ],
    };
  },
  created() {
    //초기 데이터 선언을 위한 코드 작성
    const API_KEY = "e7878598157e92ae89d1403b94d8653d";
  },
};
</script>

<style lang="scss" scoped>
@import "~/scss/main.scss";
@import "~/scss/mainview.scss";
</style>
