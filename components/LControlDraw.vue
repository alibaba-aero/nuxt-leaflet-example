<script>
export default {
  name: 'LControlDraw',
  props: {
    options: {
      type: Object,
      required: true
    }
  },
  mounted() {
    require('leaflet-draw')
    require('leaflet-draw/dist/leaflet.draw.css')

    const { L } = window
    const map = this.$parent.$parent.mapObject
    const editableLayers = this.$parent.mapObject

    const options = {
      ...this.options,
      edit: {
        featureGroup: editableLayers,
        ...this.options.edit
      }
    }

    this.mapObject = new L.Control.Draw(options)
    this.mapObject.addTo(map)

    map.on(L.Draw.Event.CREATED, (e) => {
      editableLayers.addLayer(e.layer)
      this.$emit('draw', e)
    })
  },
  beforeDestroy() {
    this.mapObject.remove()
  },
  render() {
    return null
  }
}
</script>
