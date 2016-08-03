## 一. 使用方法：

### 1.1 引入组件资源

需要在页面中首先引入radarChart.js和radarChart.css：

```
<link rel="stylesheet" type="text/css" href="radarChart.css">
```

```
<script type="text/javascript" src="radarChart.js"></script>
```

### 2.2 使用radarChart.init()方法构建雷达图：

```
radarChart.init(jsDomElement, options);
```

譬如：

```
radarChart.init(document.querySelector("#radar1"), {
    data: {
        maxValue: [100, 100, 100, 100, 100, 200],
        value: [30, 20, 40, 20, 100, 22],
        description: ["第一名", "第二名", "第三名", "第四名", "第五名", "第六名"],
        tooltipsString: function(description, value, maxVlaue) {
            return "排名：" + description + "<br>" + "分数：" + value + "<br>" + "最高分： " + maxVlaue;
        }
    },
    config: {
        scale: 0.6
    }
});
```

使用radarChart.init()方法可以构建新的雷达图。

## 二. radarChart.init()的参数说明：

**radarChart.init(jsDomElement, options)**方法接受两个参数，分别是：

|参数|类型|说明|是否必填|
| ---- | ---- | ---- | ---- |
|jsDomElement|JS原生DOM元素|雷达图构造元素|是|
|options|Object|雷达图配置信息对象|是|

### 在radarChart.init()方法中，options参数对象的属性值如下：

|参数|类型|说明|是否必填|
| ---- | ---- | ---- | ---- |
|**data**|Object|雷达图的原始数据集合对象|是|
|**config**|Object|雷达图的样式配置信息对象|可选|

### options参数中，data对象的属性值如下：

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**maxValue**|Array|数据值的最大值。如：[100, 100, 100, 100, 100]。|可选|无|
|**value**|Array|雷达图配置信息对象|可选|无|
|**description**|Array|雷达图配置信息对象|可选|无|
|**tooltipsString**|Function或String|tooltip的文字信息。当该参数类型为String时，直接显示该文字。当参数类型为Function时，该函数有3个默认参数，分别是description、value、maxVlaue，即：数据描述信息、数据值、数据最大值。需要在该函数中返回String。例如，function(description, value, maxVlaue) {return description + "<br>" + value + "<br>" + maxVlaue}。|可选|无|

### options参数中，config对象的属性值如下：

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**showTooltip**|Boolean|是否显示气泡框。为true则显示气泡框。如：[100, 100, 100, 100, 100]。|可选|true|
|**radius**|Int|雷达图的半径。|可选|无|
|**origin**|Array|中心位置[x, y]。|可选|构建元素的中心位置|
|**scale**|Float|雷达图的放大倍数。取值范围为0~1。|可选|1|
|**bg**|Object|雷达背景图配置。|可选|无|
|**dataLine**|Object|数据线条的样式配置。|可选|无|
|**dataCircle**|Object|数据点圆圈的样式配置。|可选|无|
|**tooltip**|Object|tooltip的样式配置。|可选|无|

**bg参数对象的属性值有：**

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**layer**|Int|雷达图的绘制层数。|可选|7|
|**evenFillStyle**|String|偶数层的填充样式。如："red"、"#ccc"。|可选|"#fff"|
|**oddFillStyle**|String|奇数层的填充样式。|可选|"#eee"|
|**evenStrokeStyle**|String|偶数层的描边样式。|可选|"#ddd"|
|**oddStrokeStyle**|String|奇数层的填充样式。|可选|"#ddd"|

**dataLine参数的属性值有：**

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**strokeStyle**|Int|线条样式。|可选|"red"|
|**lineWidth**|String|线条宽度。|可选|2|

**dataCircle参数的属性值有：**

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**r**|Int|圆圈半径。|可选|5|
|**strokeStyle**|String|圆圈描边样式。|可选|"red"|
|**fillStyle**|Int|圆圈填充样式。|可选|3|
|**lineWidth**|Int|圆圈线条宽度。|可选|"#fff"|

**tooltip参数的属性值有：**

|参数|类型|说明|是否必填|默认值|
| ---- | ---- | ---- | ---- | ---- |
|**offsetX**|Int|圆圈半径。|可选|0|
|**offsetY**|Int|圆圈描边样式。|可选|0|
|**r**|Int|圆圈填充样式。|可选|数据点圆圈的半径|