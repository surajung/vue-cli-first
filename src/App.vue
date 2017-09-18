<template>
  <div id="app">
    <div id="information">
      <div id="current-weather">
        <current-weather/>
      </div>
      <hr/>
      <div id="forecast">
        <forecast/>
      </div>
    </div>
    <div id="map">
        <google-map/>
    </div>
  </div>
</template>

<script>
import CurrentWeather from '@/components/CurrentWeather'
import GoogleMap from '@/components/GoogleMap'
import Forecast from '@/components/Forecast'
export default {
  name: 'app',
  components: {
    CurrentWeather,
    GoogleMap,
    Forecast
  }
}
</script>

<style lang="scss">
html {height:100%;}
body {display:flex;height:100%;background-color:#fafafa;align-items: center;justify-content: center;box-sizing:border-box;}
#app {display:inline-block;width:800px;height:600px;border-radius:10px;background-color:#444;overflow:hidden;}
#information {float:left;width:400px;}
#information:after {content:'';display:block;clear:both;}
#current-weather {display:flex;height:200px;align-items: center;justify-content: center;}
#forecast {height:400px;}
#map {float:right;width:400px;height:600px;}
hr {width:90%;}
</style>
