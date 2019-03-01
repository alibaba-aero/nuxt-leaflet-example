<template>
  <div class="container">
    <LMapSsr
      ref="map"
      class="map"
      :zoom="zoom"
      :center="center"
    >
      <LTileLayer :url="url" />

      <LFeatureGroup>
        <LControlDraw :options="drawOptions" @draw="onDraw" />
      </LFeatureGroup>
    </LMapSsr>
  </div>
</template>

<script>
import 'leaflet/dist/leaflet.css'
import { LMapSsr, LTileLayer, LFeatureGroup } from '@alibaba-aero/vue2-leaflet/src'
import LControlDraw from '~/components/LControlDraw'

export default {
  components: {
    LMapSsr,
    LTileLayer,
    LFeatureGroup,
    LControlDraw
  },
  data() {
    return {
      zoom: 3,
      center: [51.505, -0.09],
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png'
    }
  },
  computed: {
    drawOptions() {
      return {
        position: 'topleft',
        draw: {
          polyline: true,
          polygon: {
            allowIntersection: false, // Restricts shapes to simple polygons
            drawError: {
              color: '#e1e100', // Color the shape will turn when intersects
              message: '<strong>Oh snap!<strong> you can\'t draw that!' // Message that will show when intersect
            }
          },
          circle: true, // Turns off this drawing tool
          rectangle: true
        },
        edit: {
          remove: true
        }
      }
    }
  },
  methods: {
    onDraw(e) {
      console.log(e)
    }
  }
}
</script>
