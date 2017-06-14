---
title: 百度地图练习
date: 2017-06-10 20:54:29
tags: javascript
categories:
---
### 百度地图的引入

	  <script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=ir7jFwBM0tPkLebXl3ScT9cB">
	    </script>
	
	    <script type="text/javascript" src="http://api.map.baidu.com/library/SearchInfoWindow/1.5/src/SearchInfoWindow_min.js"></script>
	    <link rel="stylesheet" href="http://api.map.baidu.com/library/SearchInfoWindow/1.5/src/SearchInfoWindow_min.css" />
1. 创建地图实例：BMap.Map("container")

创建一个地图实例，container指容器id，之后调用Map.centerAndZoom()方法对地图进行初始化。未进行初始化的地图将不能进行任何操作。

1. 地图经纬度：BMap.Point

2. 以指定的经度和纬度创建一个地理点坐标。

3. 初始化地图：map.centerAndZoom(center:Point,Zoom:Number)

初始化地图，他有种设置参数方式，一是center类型为Point时，zoom必须赋值，范围3-19级，还有就是如果center类型为字符串时，比如“北京”，zoom可以忽略，地图将自动根据center适配最佳zoom级别。

	window.onload = function(){
		var map = new BMap.Map("container");
		var point = new BMap.Point(116.404, 39.915);
		map.centerAndZoom(point, 15); //map.centerAndZoom("北京");
	}



### 为地图批量添加标注(baidumap.html)
- 原理：通过for循环的方式为地图批量添加标注
- 设置点的新图标：
	- 构造出Icon对象：Icon（url:String,size:Size[,opts:IconOptions]）
	- 改变图标大小：setImageSize（offset：Size）；
	- 加载图标到地图上：setIcon（icon：Icon）
<!--more-->

var marker = new BMap.Marker(point);
map.addOverlay(marker);//添加一个覆盖物
marker.setAnimation(BMAP_ANIMATION_DROP);
var icon = new BMap.Icon("../marker.png");

### 地图配置 ###

百度地图提供许多配置方法，地图拖拽、滚轮放大缩小、双击放大、键盘操作等等，默认开启了地图拖拽、双击放大、双指操作缩放、自动适应容器尺寸变化自动适应容器尺寸变化

开启地图拖拽：map.enableDragging()；
禁止地图拖拽：map.disableDragging()；
开启滚轮放大缩小：map.enableScrollWheelZoom()；

### 控件使用 ###
百度地图提供控件：平移缩放（NavigationControl）、比例尺（ScaleControl）、缩略地图（OverviewMapControl）、地图类型（MapTypeControl）、版权（CopyrightControl等等。

1.添加平移缩放控件
 map.addControl(new BMap.NavigationControl(opts));

2.改变控件位置
Size（width：Number,height:Number）,构造Size对象，width代表水平方向数值，height代表垂直方向数值。

3.












