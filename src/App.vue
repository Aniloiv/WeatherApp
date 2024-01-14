<script setup>
import WeatherSummary from "@/components/WeatherSummary.vue";
import Highlights from "@/components/Highlights.vue";
import Coordinates from "@/components/Coordinates.vue";
import Humidity from "@/components/Humidity.vue";
import { capitalizeFirstLetter } from "@/utils";
import { ref, onMounted, computed } from "vue";
const WEBHOOK = import.meta.env.VITE_API_KEY;
const BASE_URL = import.meta.env.VITE_BASE_URL;
const city = ref("Chisinau");
const weatherInfo = ref(null);
const isError = computed(() => weatherInfo.value?.cod !== 200);

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
            <section
              :class="['section', 'section-left', { 'section-error': isError }]"
            >
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
                <WeatherSummary v-if="!isError" :weatherInfo="weatherInfo" />
                <div v-else class="error">
                  <div class="error_title">Oooops! Something went wrong!</div>
                  <div class="error_message">
                    {{ capitalizeFirstLetter(weatherInfo?.message) }}
                  </div>
                </div>
              </div>
            </section>
            <section class="section section-right" v-if="!isError">
              <Highlights :weatherInfo="weatherInfo" />
            </section>
          </div>
          <div class="sections" v-if="!isError">
            <section class="section-bottom">
              <Coordinates :coord="weatherInfo.coord" />
            </section>
            <section class="section-bottom">
              <Humidity :humidity="weatherInfo.main" />
            </section>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style lang="sass">
@import '@/assets/styles/main'

.error
    padding-top: 20px

    .error_title
      font-size: 18px
      font-weight: 700

      .error_message
        font-size: 10px
</style>
