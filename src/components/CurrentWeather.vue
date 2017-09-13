<template>
  <div>
    <div class="location">{{ location }}</div>
    <div class="weather">{{ weather }}</div>
    <div class="temp">{{ temp }}</div>
  </div>
</template>

<script>
  export default {
    name: 'current-weather',
    data () {
      return {
        location: 'Seoul',
        weather: 'Rain',
        temp: '30C',
        lat: 37.566535,
        lon: 126.977969
      }
    },
    mounted () {
      this.axios.get('http://api.openweathermap.org/data/2.5/weather', {
        params: {
          lat: this.lat,
          lon: this.lon,
          APPID: 'b05477e850237278dd6a394f39f05c8e'
        }
      })
      .then(response => {
        let data = response.data
        console.log(data)
        this.location = data.name
        this.weather = data.weather[0].main
        this.temp = (data.main.temp - 273.15).toFixed(0)
      })
    }
  }
</script>


<style>
.location{text-align:center;font-size:30px;color:#fff;}
.weather{text-align:center;font-size:20px;color:#fff;}
.temp{text-align:center;font-size:50px;color:#fff;}
</style>
