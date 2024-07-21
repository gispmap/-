<template>
  <Header></Header>
  <div id="map"></div>
</template>

<script setup>
  import Header from './components/Header.vue'
  import mapboxgl from 'mapbox-gl';
  import 'mapbox-gl/dist/mapbox-gl.css';
  import { onMounted } from 'vue';

  onMounted(()=>{
    const token = import.meta.env.VITE_TOKEN;
    mapboxgl.accessToken = token;

    const map = new mapboxgl.Map({
      container: 'map',
      style: 'mapbox://styles/mapbox/dark-v11',
      center: [114.3, 30.5],
      zoom: 9,
      pitch: 45,
      projection: 'globe'
    });

    map.on('style.load', ()=>{
      map.setFog({})
    });
  })
</script>

<style scoped>
  #map{
    width: 100vw;
    height: 100vh;
  }
</style>
