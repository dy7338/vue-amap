<script lang="ts">
import {defineComponent} from "vue";
import registerMixin from '../../../../mixins/register-component';

export default defineComponent({
  name: 'ElAmapLayerWms',
  mixins: [registerMixin],
  props: {
    url: {
      type: String
    }, // wms服务的url地址，如' https://ahocevar.com/geoserver/wms '
    blend: {
      type: Boolean,
      default: false
    }, // 地图级别切换时，不同级别的图片是否进行混合，如图层的图像内容为部分透明请设置为false
    params: {
      type: Object
    }, // OGC标准的WMS地图服务的GetMap接口的参数，包括VERSION、LAYERS、STYLES、FORMAT、TRANSPARENT等
    zooms: {
      type: Array
    }, // 支持的缩放级别范围，默认范围 [2-30]
    opacity: {
      type: Number
    } // 透明度，默认 1
  },
  data() {
    return {
    };
  },
  methods: {
    __initComponent(options) {
      this.$amapComponent = new AMap.TileLayer.WMS(options);
      this.$parentComponent.add(this.$amapComponent);
    },
    destroyComponent() {
      if(!this.parentInstance.isDestroy){
        this.$parentComponent.remove(this.$amapComponent);
      }
      this.$amapComponent = null;
      this.$parentComponent = null;
    }
  },
  render(){
    return null;
  }
});
</script>
