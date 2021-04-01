#OpenLayers教程
##一、实现简单的地图显示
1、下载OpenLayers，打开OpenLayers官网：<https://openlayers.org/>,然后点击Get the Code下载
***
2、新建HTML文件，代码里引入了ol.js和ol.css文件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Simple Map</title>
    <link rel="stylesheet" href="../v5.3.0/css/ol.css" />
    <script src="../v5.3.0/build/ol.js"></script>
</head>
<body>
    <div id="map" style="width:1000px;height:800px;"></div>
    <script>
        let map = new ol.Map({
            target: 'map',  // 关联到对应的div容器
            layers: [
                new ol.layer.Tile({   // 瓦片图层
                    source: new ol.source.OSM()    //OpenStreetMap数据源
                })
            ],
            view: new ol.View({    // 地图视图
                projection: 'EPSG:3857',
                center: [0, 0],
                zoom: 0
            }),
            controls: ol.control.defaults().extend([   // 往地图增加滑块缩放控件
                new ol.control.ZoomSlider()
            ])
        });
    </script>
</body>
</html>
<!-- 调用了ol.Map类生成了一个地图容器对象，通过target参数关联到div容器（id为"map"的div元素） -->

```
***
3、直接打开HTML文件即可看到页面地图加载
##二、地图控件
OpenLayers封装了很多控件用于对地图进行操作、显示地图信息等。

控件是一个地图上可见的小部件，其DOM元素位于屏幕上的固定位置。它们可以包含用户输入（以按钮的形式），也可以只提供信息。控件的位置是使用CSS来确定，当然也可以使用CSS来调整。默认情况下，控件被放置在地图控件层（地图控件层在上一篇文章讲过），也就是CSS类名为ol-overlayContainer-stopEvent的元素中，但也可以调整，使控件基于外部DOM元素来实现。
***
• module:ol/control/Attribution-Attribution
• module:ol/control/FullScreen-FullScreen
• module:ol/control/MousePosition-MousePosition
• module:ol/control/OverviewMap-OverviewMap
• module:ol/control/Rotate- Rotate
• module:ol/control/ScaleLine-ScaleLine
• module:ol/confrol/ZoomSlider-ZoomSlider
• module:ol/confrol/ZoomToExtent-ZoomToExtent
• module:ol/confrol/Zoom-Zoom

• 归属控件（Attribution） —— 用于展示地图资源的版权或者归属，它会默认加入到地图中。
• 全屏控件（FullScreen） —— 控制地图全屏展示
• 坐标拾取控件（MousePosition） —— 用于在地图上拾取坐标
• 鹰眼控件（OverviewMap） —— 生成地图的一个概览图
• 旋转控件（Rotate） —— 用于鼠标拖拽旋转地图，它会默认加入到地图中。
• 比例尺控件（ScaleLine） —— 用于生成地图比例尺
• 滑块缩放控件（ZoomSlider） —— 以滑块的形式缩放地图
• 缩放至特定位置控件（ZoomToExtent） —— 用于将地图视图缩放至特定位置
• 普通缩放控件（Zoom） —— 普通缩放控件，它会默认加入到地图中。
***