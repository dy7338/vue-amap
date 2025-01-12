---
title: AmapControlGeolocation
---

# AmapControlGeolocation
AMap.Geolocation 定位服务插件。融合了浏览器定位、高精度IP定位、安卓定位sdk辅助定位等多种手段，提供了获取当前准确位置、获取当前城市信息、持续定位(浏览器定位)等功能。用户可以通过两种当时获得定位的成败和结果，一种是在 getCurrentPosition的时候传入回调函数来处理定位结果，一种是通过事件监听来取得定位结果。


## Attributes

Attribute | Type | Description
---|---|---|
position| String | 控件停靠位置,默认为"RB". 'LT': 左上角, 'RT': 右上角, 'LB': 左下角, 'RB': 右下角
offset | Array | 缩略图距离悬停位置的像素距离，如 [2,2]
borderColor | String | 按钮边框颜色值，同CSS，如'silver'
borderRadius | String | 按钮圆角边框值，同CSS，如'5px'
buttonSize | String	| 箭头按钮的像素尺寸，同CSS，如'12px'
convert | Boolean	| 是否将定位结果转换为高德坐标
enableHighAccuracy | Boolean	| 进行浏览器原生定位的时候是否尝试获取较高精度，可能影响定位效率，默认为false
timeout | Number	| 定位的超时时间，毫秒
maximumAge | Number	| 浏览器原生定位的缓存时间，毫秒
showButton | Boolean	| 是否显示定位按钮，默认为true
showCircle | Boolean	| 是否显示定位精度圆，默认为true
showMarker | Boolean	| 是否显示定位点，默认为true
markerOptions | MarkerOptions	| 定位点的样式
circleOptions | CircleOptions	| 定位圆的样式
panToLocation | Boolean	| 定位成功后是否自动移动到响应位置
zoomToAccuracy | Boolean	| 定位成功后是否自动调整级别
GeoLocationFirst | Boolean	| 优先使用H5定位，默认移动端为true，PC端为false
noIpLocate | Number	| 是否禁用IP精确定位，默认为0，0:都用 1:手机上不用 2:PC上不用 3:都不用
noGeoLocation | Number	| 是否禁用浏览器原生定位，默认为0，0:都用 1:手机上不用 2:PC上不用 3:都不用
useNative | Boolean	| 是否与高德定位SDK能力结合，需要同时使用安卓版高德定位sdk，否则无效
getCityWhenFail | Boolean	| 定位失败之后是否返回基本城市定位信息
needAddress | Boolean	| 是否需要将定位结果进行逆地理编码操作
extensions | String	| 是否需要详细的逆地理编码信息，默认为'base'只返回基本信息，可选'all'
reEventWhenUpdate | Boolean | 是否在组件更新时重新注册事件，主要用于数组更新时，解决绑定了事件但事件的对象不会更新问题，默认false


## Events

Event Name | Parameters | Description
---|---|---|
complete | {statue:'', result:{}}| 定位结束后触发的事件
