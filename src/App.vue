<template>
  <div id="app">
    <header id="nav">
      <div class="content--left">
        <span @click="sidebar = !sidebar" class="hamburger"></span>
      </div>
      <h1 class="content--center">Moments</h1>
      <div class="content--right"></div>
    </header>
    <div class="sidebar" v-if="sidebar">
      <div class="circle-icon"><i class="fas fa-user"></i></div>
      <div class="circle-icon"><i class="fas fa-user"></i></div>
      <div class="circle-icon"><i class="fas fa-user"></i></div>
      <div class="circle-icon"><i class="fas fa-user"></i></div>

    </div>
    <div id='geocoder' class='geocoder'></div>
    <section id="mapbox"></section>
    <!--<router-view/>-->
  </div>
</template>

<script>
  import Mapbox from 'mapbox-gl';
  import MapboxGeocoder from 'mapbox-gl-geocoder';

  Mapbox.accessToken = 'pk.eyJ1IjoibWF4ZmF1IiwiYSI6ImNqc2RxenlzMjB3M2U0NG82cmtraXY3eDAifQ.K6MY_9q0uteTcefCZznasg';

  export default {
    data() {
      return {
        sidebar: false,
      };
    },
    mounted() {
      let map = new Mapbox.Map({
        container: 'mapbox',
        style: 'mapbox://styles/mapbox/outdoors-v9',
        zoom: 13,
        center: [3.876716, 43.610769]
      });

      var geocoder = new MapboxGeocoder({
        accessToken: Mapbox.accessToken
      });

      document.getElementById('geocoder').appendChild(geocoder.onAdd(map));

      // map.on('click', (event) => {
      //   // console.log(event)
      // })
    }
  }
</script>

<style lang="scss">

</style>
