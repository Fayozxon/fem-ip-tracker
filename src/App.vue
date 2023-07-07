<script>
import axios from 'axios';
import MapDisplay from './components/MapDisplay.vue';
import SearchBar from './components/SearchBar.vue';
import LocationInfo from './components/LocationInfo.vue';

export default {
  components: {MapDisplay, SearchBar, LocationInfo},
  data() {
    return {
      API_KEY: 'at_8bxULRLnGzz9Se7WPqMJEh9Cvpx0E',
      locationData: ''
    }
  },
  methods: {
    async loadData(ipAddress) {
      try {
        const res = await fetch(`http://ip-api.com/json/${ipAddress}?fields=status,message,country,regionName,city,lat,lon,timezone,isp,org,as,query`);
        this.locationData = res.data;
      } catch(err) {
        alert(err);
      }
    }
  },
  mounted() {
    this.loadData('');
  }
}
</script>

<template>
  
  <main>

    <section class="main-section">
      <div class="container">
        <h1 class="title">IP Address Tracker</h1>

        <!-- search -->
        <SearchBar @loadData="loadData"></SearchBar>

        <!-- location -->
        <LocationInfo :locationData="locationData"></LocationInfo>

      </div>
    </section>

    <!-- map -->
    <MapDisplay v-if="locationData" :locationData="locationData"></MapDisplay>

  </main>

</template>

<style scoped>
.main-section {
  min-height: 30vh;
  background-image: url('./assets/pattern-bg-desktop.png');
  background-repeat: no-repeat;
  background-size: cover;
  padding-top: 30px;
}

.container {
  position: relative;
}

.main-section .title {
  font-size: 2rem;
  color: var(--clr-light);
  font-weight: 700;
  letter-spacing: -2.5;
  text-align: center;
}

.main-section .search-bar {
  margin-top: 30px;
  margin-bottom: 50px;
}

.main-section .info-box {
  position: absolute;
  left: 25px;
  right: 25px;
}

/* RWD */
@media only screen and (max-width: 830px) {
  .main-section {
    min-height: 40vh;
  }

  .main-section .search-bar {
    margin-bottom: 20px;
  }
}
</style>
