<template>
  <div class="summary">
    <div
      style="
        background-image: url('/src/assets/img/weather-main/thunderstorm.png');
      "
      class="pic-main"
    ></div>
    <div class="weather">
      <div class="temp">14 °C</div>
      <div class="weather-desc text-block">Thunderstorm</div>
    </div>
    <div class="city text-block">Paris, FR</div>
    <div class="date text-block">Thu, March 16, 2023</div>
  </div>
</template>
<script>
export default {
  props: {
    weatherInfo: Object,
  },
};
</script>
