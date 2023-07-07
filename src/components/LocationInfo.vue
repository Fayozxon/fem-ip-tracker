<script>
export default {
    props: ['locationData']
}
</script>

<template>
  
  <div v-if="locationData" class="info-box">
    <div class="info-box__item">
        <h3 class="title">IP address</h3>
        <h2 class="info">{{ locationData.query }}</h2>
    </div>
    <span class="line"></span>
    <div class="info-box__item">
        <h3 class="title">Location</h3>
        <h2 class="info">{{ locationData.country + ' ' + locationData.regionName }}</h2>
    </div>
    <span class="line"></span>
    <div class="info-box__item">
        <h3 class="title">Timezone</h3>
        <h2 class="info">{{ locationData.timezone }}</h2>
    </div>
    <span class="line"></span>
    <div class="info-box__item">
        <h3 class="title">ISP</h3>
        <h2 class="info">{{ locationData.isp }}</h2>
    </div>
  </div>

</template>

<style scoped>
.info-box {
    background: var(--clr-light);
    padding: 35px 40px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.1);
    border-radius: 15px;
    display: flex;
    gap: 35px;
    align-items: start;
    justify-content: space-between;
    z-index: 10;
}

.info-box .line {
    display: inline-block;
    width: 1px;
    height: 60px;
    align-self: center;
    background: #D9D9D9;
}

.info-box__item .title {
    text-transform: uppercase;
    color: var(--clr-grey);
    font-weight: 600;
    font-size: 15px;
    letter-spacing: 2px;
}

.info-box__item .info {
    font-size: 1.5rem;
    font-weight: 700;
    padding-top: 15px;
}

/* RWD */
@media only screen and (max-width: 1000px) {
    .info-box {
        max-width: 555px;
        margin: 0 auto;
        flex-direction: column;
        text-align: center;
        align-items: center;
        gap: 20px;
        padding: 30px;
    }

    .info-box__item .title {
        font-size: 13px;
    }

    .info-box__item .info {
        font-size: 18px;
    }

    .info-box .line {
        display: none;
    }
}
</style>