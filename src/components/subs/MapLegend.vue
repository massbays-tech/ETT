<template>
  <div class="legend-border">
    <div class="row">
      <div class="col-3">
        <svg height="20" width="30">
          <rect id="legend 1" x="0" y="0" width="30" height="20" style="fill: #000000; fill-opacity: 0; stroke: #000000"/>
        </svg> 
      </div>
      <div class="col-9">
        MassBays Assessment Area
      </div>
    </div>
    <div v-for="(item, key) in imageLibraryHabitat" :key="key">
      <div v-if="habitat == key">
        <div class="row">
          <div class="col-3">
            <svg height="20" width="30">
              <rect id="legend 2" x="0" y="0" width="30" height="20" :style="{fill: item.currentColor}"/>
            </svg> 
          </div>
          <div class="col-9">
            {{ item.title }} Extent
            <br>
            ({{item.currentYear}})
          </div>
        </div>
        <div class="row">
          <div class="col-3">
            <svg height="20" width="30">
              <rect id="legend 2" x="0" y="0" width="30" height="20" :style="{fill: item.historicColor}"/>
            </svg> 
          </div>
          <div class="col-9">
            {{ item.title }} Extent
            <br>
            ({{item.historicYear}})
          </div>
        </div>
      </div>
    </div> 
    <div class="row" v-if="pointsLayer == true">
      <div class="col-3">
        <svg height="20" width="30">
          <circle id="legend 6" cx="15" cy="10" r="5" style="fill: #00B0F0"/>
        </svg> 
      </div>
      <div class="col-9">
        WQ Data Available
        <br>
        At Station
      </div>
    </div>
    <div class="row" v-if="pointsLayer == true">
      <div class="col-3">
        <svg height="20" width="30">
          <circle id="legend 6" cx="15" cy="10" r="5" style="fill: #808080"/>
        </svg> 
      </div>
      <div class="col-9">
        No WQ Data Available
        <br>
        At Station
      </div>
    </div>
  </div>
</template>

<script>
import { imageLibraryHabitat } from '../../lib/constants'
export default {
  data () {
    return {
        imageLibraryHabitat: imageLibraryHabitat
    }
  },
  computed: {
    habitat() {
      return this.$store.state.habitat;
    },
    pointsLayer() {
      return this.$store.state.pointsLayer;
    }
  }

}
</script>

<style scoped>
.legend-border {
  border: solid 1px gray;
  background-color: rgba(255,255,255,.7);
  border-radius: 10px;
  padding: 15px;
  font-size: 12px;
}

</style>
