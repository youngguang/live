# ModifyCasterComponent {#reference3151 .reference}

修改组件。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：ModifyCasterComponent|
|CasterId|String|是|导播间Id。|
|ComponentId|String|是|组件ID。|
|ComponentName|String|否|组件名称，默认为组件ID。|
|ComponentType|String|否|组件的类型，只能是预设值的一种: “text”、”image”、”caption”等。|
|Effect|String|否|组件显示的特效。-   默认值：none
-   none：无
-   animateH：水平滚动
-   animateV：垂直滚动

 |
|ComponentLayer|String|否|设置该组件Layer的尺寸，布局等信息。JSON格式字符串，参数名采用首字母大写、驼峰格式。

|
|TextLayerContent|String|否|如果组件类型是text，设置该Layer元素属性。JSON格式字符串，参数名采用首字母大写，驼峰格式。

|
|ImageLayerContent|String|否|如果组件类型是image，设置该Layer元素属性。JSON格式字符串，参数名采用首字母大写，驼峰格式。

|
|CaptionLayerContent|String|否|如果组件类型是caption，设置该Layer元素属性。JSON格式字符串，参数名采用首字母大写，驼峰格式。

|

ComponentLayer

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|HeightNormalized|Float|是|设置该layer元素的高度归一化比例值。-   取值范围\[0，1\]，其中元素的宽度会按照该高度来进行等比缩放。
-   默认值：0，表示按照元素的原始尺寸进行显示。

|
|WidthNormalized|Float|是|设置该layer元素的宽度归一化比例值。-   取值范围\[0，1\]，其中元素的高度会按照该宽度来进行等比缩放。
-   默认值：0，表示按照元素的原始尺寸进行显示。
-   该字段和heightNormalized有冲突。
-   一旦同时设置了heightNormalized和widthNormalized，只有heightNormalized生效。
-   如果heightNormalized和widthNormalized设置只能同时设置一个，后面设置的值会影响前面的设置。

|
|PositionNormalized|Float\[\]|是|设置该layer 元素的位置归一化值\[x，y\]。-   默认为\[0，0\]，其中x，y需要进行归一化计算。
-   取值范围：\[0，1\]

|
|PositionRefer|String|是|设置元素的position 参考坐标值。-   取值范围：”topLeft”、”topRight”、”bottomLeft”、”bottomRight”
-   默认值：”topLeft”

|

TextLayerContent

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Text|String|是|文本内容。默认为””。

|
|Color|String|是|文字色彩。-   取值范围：“0x000000-0xffffff”
-   默认：“0xff0000”，红色。

|
|FontName|String|是|字体名字。取系统预设值默认楷体，“KaiTi”。

|
|SizeNormalized|Float|是|字体归一化大小。-   字体设置大小为：”font\_size/output\_height”。
-   取值范围：\[0，1\]。
-   如果系统根据归一化方式反计算的出来的字体大小\>1024，取1024。

|
|BorderWidthNormalized|Float|是|文字边框宽度归一化值。-   该归一化值是基于文字的size来计算的，即BorderWidth/FontSize。
-   取值范围：\[0，1\]如果系统归一化反计算出来的值超过16，取16。
-   默认值：0

|
|BorderColor|String|是|文字边框色彩。-   取值：“0x000000-0xffffff”
-   默认：””，表示无效。

|

ImageLayerContent

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|MaterialId|String|是|媒资库素材Id|

CaptionLayerContent

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|LocationId|String|是|组件类型为caption时，表示引用的视频源Location。|
|PtsOffset|Integer|否|纠正当前字幕pts与语音pts偏差值。-   取值范围\[-10000, +10000\]
-   默认值：0

|
|WordsCount|Integer|否|显示字数，可配合字体大小调整。-   取值范围\[10，50\]
-   默认值：35

|
|Color|String|是|文字色彩。取值：“0x000000-0xffffff”，红色。

|
|FontName|String|是|字体名字，取系统预设值。默认：楷体，“KaiTi”。

|
|SizeNormalized|Float|是|字体归一化大小。-   字体设置大小为”font\_size/output\_height”
-   如果系统根据归一化方式反计算的出来的字体大小\>1024, 取1024。
-   默认值：-1，表示无效。

|
|BorderWidthNormalized|Float|是|文字边框宽度归一化值。-   该归一化值是基于文字的size来计算的，即BorderWidth/FontSize。
-   如果系统归一化反计算出来的值超过16，取16。
-   默认值：0

|
|BorderColor|String|是|文字边框色彩。-   取值：“0x000000-0xffffff”
-   默认：””，表示无效。

|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求Id|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=ModifyCasterComponent&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&ComponentName=text&LocationId=RC01&ComponentType=text&Effect=animateH&ComponentLayer=&ImageLayerContent=&<公共请求参数> 
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|
|DuplicateLocationID|LocationId is duplicate|400|LocationId重复|
|InvalidParameter.Malformed|MaterialId is not found|400|素材ID无效或不存在|

