<script lang="ts">
import {defineComponent} from "vue";
import registerMixin from '../../../mixins/register-component';
import locaMixin from '../../../mixins/loca-component';

export default defineComponent({
  name: 'ElAmapLocaPolygon',
  mixins: [registerMixin, locaMixin],
  props: {
    cullface: {
      type: String
    }, // 剔除背面/前面的面（选择剔除将会提升性能），可选：back/front/none，back是剔除背面的面，front是剔除前面的面，none是不进行剔除。
    acceptLight: {
      type: Boolean,
      default: true
    }, // 面是否接受光照，光照信息在 loca 对象中配置
    shininess: {
      type: Number
    }, // 立体网格的粗糙度，值越高，说明表面越粗糙。
    hasSide: {
      type: Boolean,
      default: true
    }, // 当面有厚度的时候，有没有侧面
    hasBottom: {
      type: Boolean,
      default: false
    },//当面有厚度的时候，有没有底面。
    blockHide: {
      type: Boolean,
      default: true
    },//是否开启被遮挡的面隐藏，默认开启，如果关闭，在有透明度的时候，会显示出被遮挡的面。
    depth: {
      type: Boolean,
      default: true
    }// 是否开启深度检测，开启后可能会影响zIndex
  },
  data() {
    return {
      converters: {},
    };
  },
  methods: {
    __initComponent(options) {
      this.$amapComponent = new Loca.PolygonLayer(options);
      this.setSource();
      this.setStyle();
      this.$parentComponent.add(this.$amapComponent);
      this.initComplete();
    },
    setStyle() {
      const defaultStyleValue = {
        topColor: '#fff',
        sideTopColor: '#fff',
        sideBottomColor: '#fff',
        altitude: 0,
        height: 0,
        texture: null,
        textureSize: [20, 3],
        label: undefined,
        labelAltitude: 0
      };
      const style = Object.assign({}, defaultStyleValue, this['defaultStyleValue']);
      const defaultLayerStyle = {
        topColor: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.topColor === undefined ? style.topColor : feature.properties.topColor;
        },
        sideTopColor: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.sideTopColor === undefined ? style.sideTopColor : feature.properties.sideTopColor;
        },
        sideBottomColor: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.sideBottomColor === undefined ? style.sideBottomColor : feature.properties.sideBottomColor;
        },
        altitude: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.altitude === undefined ? style.altitude : feature.properties.altitude;
        },
        height: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.height === undefined ? style.height : feature.properties.height;
        },
        texture: style.texture,
        textureSize: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.textureSize === undefined ? style.textureSize : feature.properties.textureSize;
        },
        label: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.label === undefined ? style.label : feature.properties.label;
        },
        labelAltitude: (index, feature) => {
          feature.properties = feature.properties || {};
          return feature.properties.labelAltitude === undefined ? style.labelAltitude : feature.properties.labelAltitude;
        }
      };
      const layerStyle = Object.assign({}, defaultLayerStyle, this['layerStyle']);
      this.$amapComponent.setStyle(layerStyle);
    }
  },
  render() {
    return null;
  }
});
</script>
