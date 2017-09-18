<template>
  <div>
    <ul class="forecasts">
      <li class="item" v-for="forecast in forecasts" :key="forecast.dt">
        <div class="weekday">{{ convertToDate(forecast.dt) | weekday }}</div>
        <div class="icon">
          <img :src="`http://openweathermap.org/img/w/${forecast.weather[0].icon}.png`" />
        </div>
        <div class="temp">{{ (forecast.temp.day - 273.15).toFixed(0) }}</div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'forecast',
  data () {
    return {
      lat: 37.566535,
      lon: 126.977969,
      forecasts: []
    }
  },
  methods: {
    convertToDate (timestamp) {
      return new Date(timestamp * 1000)
    },
    setCoordinate (coordinate) {
      this.lat = coordinate.lat
      this.lon = coordinate.lng
      this.axios.get('http://api.openweathermap.org/data/2.5/forecast/daily', {
        params: {
          lat: this.lat,
          lon: this.lon,
          APPID: 'c5d698f455ddeab167e90c6f9a276f3e'
        }
      })
      .then(response => {
        const data = response.data
        this.forecasts = data.list
      })
    }
  },
  filters: {
    weekday (date) {
      let weekdayNames = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']
      return weekdayNames[date.getDay()]
    }
  },
  mounted () {
    this.$bus.$on('sendCoordinate', this.setCoordinate)
  }
}
</script>
<style scoped>
.forecasts {padding:10px 0 0;margin:0;text-align:center}
.forecasts .item {display:inline-block;padding:5px 0;color:#fff;}
.forecasts li.item:first-child {font-weight:bold;background-color:#666;border-radius:5px;}
</style>