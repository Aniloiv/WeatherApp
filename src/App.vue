<script setup>
import WeatherSummary from "@/components/WeatherSummary.vue";
import Highlights from "@/components/Highlights.vue";
import Coordinates from "@/components/Coordinates.vue";
import Humidity from "@/components/Humidity.vue";
import { ref, onMounted } from "vue";
const WEBHOOK = import.meta.env.VITE_API_KEY;
const BASE_URL = import.meta.env.VITE_BASE_URL;
const city = ref("Chisinau");
const weatherInfo = ref(null);

function getWeather() {
  fetch(`${BASE_URL}?q=${city.value}&appid=${WEBHOOK}&units=metric`)
    .then((response) => response.json())
    .then((data) => (weatherInfo.value = data));
}
onMounted(getWeather);
</script>

<template>
  <div class="page">
    <main class="main">
      <div class="container">
        <div class="laptop">
          <div class="sections">
            <section class="section section-left">
              <div class="info">
                <div class="city-inner">
                  <input
                    type="text"
                    class="search"
                    v-model="city"
                    @keyup.enter="getWeather"
                  />
                  <span class="search_ico" @click="getWeather">
                    <img src="/src/assets/img/search.svg" alt="search" />
                  </span>
                </div>
                <WeatherSummary :weatherInfo="weatherInfo" />
              </div>
            </section>
            <section class="section section-right">
              <Highlights />
            </section>
          </div>
          <div class="sections">
            <section class="section-bottom">
              <Coordinates />
            </section>
            <section class="section-bottom">
              <Humidity />
            </section>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style lang="sass">
@import '@/assets/styles/main'
</style>
