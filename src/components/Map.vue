<template>
  <div id="mapContainer">
    <div id="map"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  mounted() {
    if (window.kakao && window.kakao.maps) {
      this.initMap();
    } else {
      const script = document.createElement("script");
      /* global kakao */
      script.onload = () => kakao.maps.load(this.initMap);
      script.src =
        "http://dapi.kakao.com/v2/maps/sdk.js?autoload=false&appkey=34378d05122dfeb335f5898eb958346d";
      document.head.appendChild(script);
    }
  },
  methods: {
    initMap() {
      var mapContainer = document.getElementById("map"), // 지도를 표시할 div
        mapOption = {
          center: new kakao.maps.LatLng(37.564343, 126.947613), // 지도의 중심좌표
          level: 3, // 지도의 확대 레벨
        };

      var map = new kakao.maps.Map(mapContainer, mapOption);

      var positions = [
        {
          //서울
          latlng: new kakao.maps.LatLng(37.5683, 126, 9778),
        },
        {
          //인천
          latlng: new kakao.maps.LatLng(37.40864282648822,126.65071862847725),
        },
        {
          //수원
          latlng: new kakao.maps.LatLng(37.2911,127.0089),
        },
        {
          //대전
          latlng: new kakao.maps.LatLng(36.3519957815787,127.39131469478555),
        },
        {
          //태백
          latlng: new kakao.maps.LatLng(37.15818414766273,128.928560966107),
        },
        {
          //강릉
          latlng: new kakao.maps.LatLng(37.791688035246636,128.82867301427635),
        },
      ];

      //마커를 생성합니다.
      positions.forEach(function (pos) {
        var marker = new kakao.maps.Marker({
          position: pos.latlng, //마커의 위치

          marker.setMap(map);
        });
      });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~/scss/main.scss";
#mapContainer {
  @include center;
  width: 100%;
  height: 35%;
  #map {
    width: 80%;
    height: 90%;
    border-radius: 10px;
  }
}
</style>
