---
title: AmapBezierCurve
---

# AmapBezierCurve
贝塞尔曲线

## Attributes

Attribute | Type | Description
---|---|---|
bubble | Boolean | 是否将覆盖物的鼠标或touch等事件冒泡到地图上 默认 false
editOptions | Object | [设置编辑参数参数](https://a.amap.com/jsapi/static/doc/20210906/index.html?v=2#polylineeditor)
visible | Boolean | 是否可见
editable | Boolean | 折线当前是否可编辑
path | Array | 贝瑟尔曲线的路径。描述为一个二维数组规则如下：第一个元素是起点， 之后的元素同时描述控制点和途经点，之后每个元素可以有0个到2个控制点 控制点在前，途经点在最后 [ [lng,lat] ,//起点0 [lng,lat,lng,lat,lng,lat] ,//控制点、控制点、途经点2 [lng,lat,lng,lat] //控制点、途经点3 ] 或者 [ [ [lng,lat] ],//起点0 [ [lng,lat] , [lng,lat] ],//控制点、途经点1 [ [lng,lat] , [lng,lat] , [lng,lat] ],//控制点、控制点、途经点2 [ [lng,lat] , [lng,lat] ]//控制点、途经点3 ]
zIndex | Number | 折线覆盖物的叠加顺序。默认叠加顺序，先添加的线在底层，后添加的线在上层。通过该属性可调整叠加顺序，使级别较高的折线覆盖物在上层显示。默认zIndex：10
strokeColor | String | 线条颜色，使用16进制颜色代码赋值。默认值为#006600
strokeOpacity | Number | 线条透明度，取值范围[0,1]，0表示完全透明，1表示不透明。默认为0.9
strokeWeight | Number | 线条宽度，单位：像素
borderWeight | Number | 描边线宽度
isOutline | Boolean | 线条是否带描边，默认false
outlineColor | String | 线条描边颜色，此项仅在isOutline为true时有效，默认：#000000
draggable | Boolean | 设置多边形是否可拖拽移动，默认为false
strokeStyle | String | 线样式，实线:solid，虚线:dashed
strokeDasharray	| Array | 勾勒形状轮廓的虚线和间隙的样式，此属性在strokeStyle 为dashed 时有效， 此属性在ie9+浏览器有效 取值： 实线： [0,0,0] 虚线： [10,10] ， [10,10] 表示10个像素的实线和10个像素的空白（如此反复）组成的虚线 点画线： [10,2,10] ， [10,2,10] 表示10个像素的实线和2个像素的空白 + 10个像素的实线和10个像素的空白 （如此反复）组成的虚线
lineJoin | String | 折线拐点的绘制样式，默认值为'miter'尖角，其他可选值：'round'圆角、'bevel'斜角
lineCap | String | 折线两端线帽的绘制样式，默认值为'butt'无头，其他可选值：'round'圆头、'square'方头
geodesic | Boolean | 是否绘制大地线，默认false
showDir | Boolean | 是否延路径显示白色方向箭头,默认false。建议折线宽度大于6时使用
extData | any | 用户自定义属性，支持JavaScript API任意数据类型，如Polygon的id等
reEventWhenUpdate | Boolean | 是否在组件更新时重新注册事件，主要用于数组更新时，解决绑定了事件但事件的对象不会更新问题，默认false

## Events

Event Name | Parameters | Description
---|---|---|
init | Object | 高德组件实例
click | MapsEvent | 鼠标左键单击事件
dblclick | MapsEvent | 鼠标左键双击事件
rightclick | MapsEvent | 鼠标右键单击事件
hide | {type, target} | 隐藏
show | {type, target} | 显示
mousedown | MapsEvent | 鼠标按下
mouseup | MapsEvent | 鼠标抬起
mouseover | MapsEvent | 鼠标经过
mouseout | MapsEvent | 鼠标移出
touchstart | MapsEvent | 触摸开始时触发事件，仅适用移动设备
touchmove | MapsEvent | 触摸移动进行中时触发事件，仅适用移动设备
touchend | MapsEvent | 触摸结束时触发事件，仅适用移动设备
addnode |	{target: Polygon, lnglat: Lnglat, pixel: Pixel} | 	编辑状态下，通过鼠标在折线上增加一个节点或在多边形上增加一个顶点时触发此事件
removenode | {target: Polygon, lnglat: Lnglat, pixel: Pixel} |	编辑状态下，通过鼠标在折线上删除一个节点或在多边形上删除一个顶点时触发此事件
adjust |	{target: Polygon, lnglat: Lnglat, pixel: Pixel} |	编辑状态下，鼠标调整折线上某个节点或多边形上某个顶点的位置时触发此事件
add | {target: target} | 创建一个覆盖物之后触发该事件，target即为创建对象。当editor编辑对象为空时，调用open接口，再点击一次屏幕就会创建新的覆盖物对象
end |	{type,target}	 | 关闭编辑状态，触发该事件，target即为编辑后的折线/多边形对象

