<template>
  <div class="map-container">
    <el-amap
      v-model:zoom="zoom"
      v-model:rotation="rotation"
      v-model:center="center"
      v-model:pitch="pitch"
      :show-label="false"
      view-mode="3D"
      :terrain="true"
      @click="clickMap"
      @init="initMap"
      @complete="completeMap"
      @moveend="moveendMap"
    >
      <el-amap-control-control-bar />
      <el-amap-control-hawk-eye :is-open="eyeOpen" />
      <el-amap-control-map-type />
      <el-amap-control-scale />
      <el-amap-control-tool-bar />
      <el-amap-search-box
        input-id="search"
        :input-custom="true"
        @select="selectSearch"
      />
      <el-amap-control-geolocation @complete="getLocation" />
    </el-amap>
    <div class="control-container">
      <el-button @click="changeCenter">
        更换中心点
      </el-button>
      <el-button @click="changeEyeOpen">
        鹰眼显隐
      </el-button>
      <input id="search">
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import ElAmapSearchBox from "@vue-map/packages/control/SearchBox/SearchBox.vue";
import ElAmapControlGeolocation from "@vue-map/packages/control/Geolocation/Geolocation.vue";
import ElAmap from '../../src/packages/amap/amap.vue'
import ElAmapControlControlBar from "../../src/packages/control/ControlBar/ControlBar.vue";
import ElAmapControlHawkEye from "../../src/packages/control/HawkEye/HawkEye.vue";
import ElAmapControlMapType from "../../src/packages/control/MapType/MapType.vue";
import ElAmapControlScale from "../../src/packages/control/Scale/Scale.vue";
import ElAmapControlToolBar from "../../src/packages/control/ToolBar/ToolBar.vue";
import ElAmapGeolocation from "../../src/packages/control/Geolocation";

export default defineComponent({
  name: "Map",
  components: {
    ElAmapControlGeolocation,
    ElAmapSearchBox,
    ElAmapControlToolBar,
    ElAmapControlScale, ElAmapControlMapType, ElAmapControlHawkEye, ElAmapControlControlBar, ElAmap,ElAmapGeolocation},
  data(){
    return {
      center: [120,31],
      zoom: 16,
      pitch: 50,
      rotation: 0,
      eyeOpen: true,
    }
  },
  methods: {
    clickMap(e){
      console.log('click map: ', e);
    },
    initMap(map){
      console.log('init map: ', map);
    },
    completeMap(e){
      console.log(e);
    },
    moveendMap(e){
      console.log('moveendMap: ', e);
    },
    changeCenter(){
      const lng = this.center[0]+0.01;
      const lat = this.center[1]+0.01;
      this.center = [lng, lat];
    },
    changeEyeOpen(){
      this.eyeOpen = !this.eyeOpen;
    },
    selectSearch(e){
      console.log('search: ', e);
    },
    getLocation(e){
      console.log('getLocation: ', e);
    }
  }
})
</script>

<style scoped>
.map-container{
  width: 100%;
  height: 100%;
  position: relative;
}
.control-container{
  position: absolute;
  padding: 24px;
  background: #ffffff;
  z-index: 2;
  bottom: 40px;
  left: 150px;
  right: 150px;
}
</style>
