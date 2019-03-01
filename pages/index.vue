<template>
  <div class="container">
    <LMapSsr
      ref="map"
      class="map"
      :zoom="zoom"
      :center="center"
    >
      <LTileLayer :url="url" />
    </LMapSsr>
  </div>
</template>

<script>
import 'leaflet/dist/leaflet.css'
import { LMapSsr, LTileLayer } from '@alibaba-aero/vue2-leaflet/src'

export default {
  components: {
    LMapSsr,
    LTileLayer
  },
  data() {
    return {
      zoom: 15,
      center: [47.413220, -1.219482],
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png'
    }
  },
  mounted() {
    this.getLocation()
  },
  methods: {
    getLocation() {
      navigator.geolocation.getCurrentPosition(({ coords }) => {
        this.center = [ coords.latitude, coords.longitude ]
      })
    }
  }
}

</script>
