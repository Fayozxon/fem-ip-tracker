<script>
import { ref, onMounted, watch } from 'vue';
import "leaflet/dist/leaflet.css";
import L from "leaflet";

export default {
  props: ['locationData'],
  setup(props) {
    const lat = ref(props.locationData.lat);
    const lng = ref(props.locationData.lon);

    let map;

    const initialMap = () => {
      map = L.map('map');
      map.setView([lat.value, lng.value], 13);
      L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
      }).addTo(map);

      L.marker([lat.value, lng.value]).addTo(map).openPopup();
    };

    const makeMap = () => {
      map.setView([lat.value, lng.value], 13);

      L.marker([lat.value, lng.value]).addTo(map).openPopup();
    };

    onMounted(() => {
      initialMap();
    });

    watch(() => props.locationData, (newData) => {
      lat.value = newData.lat;
      lng.value = newData.lon;
      makeMap();
    });
  }
};
</script>


<template>
  <div class="map" id="map"></div>

</template>

<style scoped>
.map {
  position: relative;
  width: 100vw;
  height: 70vh;
  z-index: 5;
}

/* RWD */
@media only screen and (max-width: 830px) {
  .map {
    height: 100vh;
  }
}
</style>