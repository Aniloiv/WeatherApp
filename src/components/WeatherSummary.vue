<template>
  <div class="summary">
    <div
      :style="`background-image: url('/src/assets/img/weather-main/${weatherInfo.weather[0]?.description}.png');`"
      class="pic-main"
    ></div>
    <div class="weather">
      <div class="temp">{{ weatherInfo?.main?.temp.toFixed(0) }} °C</div>
      <div class="weather-desc text-block">
        {{ capitalizeFirstLetter(weatherInfo.weather[0]?.description) }}
      </div>
    </div>
    <div class="city text-block">
      {{ weatherInfo?.name }}, {{ weatherInfo?.sys?.country }}
    </div>
    <div class="date text-block">{{ today }}</div>
  </div>
</template>
<script setup>
import { capitalizeFirstLetter } from "@/utils/index";
const props = defineProps({
  weatherInfo: {
    type: [Object, null],
    required: true,
  },
});
const today = new Date().toLocaleString("en-EN", {
  weekday: "short",
  year: "numeric",
  month: "long",
  day: "numeric",
});
</script>
