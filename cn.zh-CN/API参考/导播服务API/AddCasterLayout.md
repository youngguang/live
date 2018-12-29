# AddCasterLayout {#reference2970 .reference}

添加导播台布局。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：AddCasterLayout|
|CasterId|String|是|导播台Id|
|VideoLayers|\[\]VideoLayer|是|Videolayer配置列表，元素为视频画面的配置信息，如宽高、位置等，画面层次按列表顺序排列|
|AudioLayers|\[\]AudioLayer|是|Audiolayer配置列表，元素为音频配置信息，无层次关系|
|BlendLists|\[\]String|是|元素为资源的位置ID（locationId参见添加视频源），与VideoLayers元素顺序对应|
|MixLists|\[\]String|是|元素为资源的位置ID（locationId参见添加视频源），与VideoLayers元素顺序对应|

VideoLayer

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|FillMode|String|否|元素填充方式。-   不填充：”none”
-   自适应：”fit”

默认：不填充。

-   若采用不填充模式，则以画面作为配置目标进行Layer设置。
-   若采用自适应模式，则以填充区（框）作为配置目标进行Layer设置，此时画面会按照原始的宽高比缩放，长边对齐的自适应方式在填充区（框）内居中填充。若填充区宽高比和画面不一致，则短边两侧无填充（显示为下层Layer画面，若下层未配置Layer，默认为底图黑色）。

|
|HeightNormalized|Float|否|设置该layer元素的高度归一化比例值。-   若采用不填充模式，元素的宽度会按照该高度来进行等比缩放，默认值：0，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式时，该字段必输且大于0，表示填充区\(框\)高度归一化比例值。

|
|WidthNormalized|Float|否|设置该layer元素的宽度归一化比例值。-   若采用不填充模式，元素的高度会按照该宽度来进行等比缩放，默认值：0，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式时，该字段必输且大于0，表示填充区\(框\)宽度归一化比例值。

|
|PositionNormalized|\[\]Float|否|设置该layer 元素的位置归一化值\[x，y\]。默认值：\[0，0\]

**说明：** x，y需要进行归一化计算。

 |
|PositionRefer|String|否|设置元素的position 参考坐标值。-   取值范围：topLeft，topRight，bottomLeft，bottomRight以及center，topCenter，bottomCenter，leftCenter，rightCenter。
-   默认值：topLeft

|
|FixedDelayDuration|Integer|否|该字段对视频进行固定延迟设置，可用于字幕同步。-   单位：ms
-   默认值：0
-   取值范围：\[0-5000\]

|

AudioLayer

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|VolumeRate|Float|是|调节音频流的音量大小倍数。-   1.0：表示保持原有音量。
-   小于1：表示降低音量的倍数。
-   大于1：表示放大的倍数。

取值范围：\[0, 10.0\]

默认值：1.0

|
|ValidChannel|String|是|确定哪些声道可以作为音量输入。-   取值范围：leftChannel，rightChannel，all
-   默认值：all

|
|FixedDelayDuration|Integer|否|该字段对视频进行固定延迟设置，可用于字幕同步。-   单位：ms
-   默认值：0
-   取值范围：\[0-5000\]

|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|LayoutId|String|布局Id|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=AddCasterLayout&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&AudioLayer.1.ValidChannel=all&AudioLayer.1.VolumeRate=1&AudioLayer.2.ValidChannel=all&AudioLayer.2.VolumeRate=1&VideoLayer.1.HeightNormalized=1&VideoLayer.1.WidthNormalized=1&VideoLayer.1.PositionNormalized.1=0.0&VideoLayer.1.PositionNormalized.2=0.3&VideoLayer.2.HeightNormalized=1&VideoLayer.2.WidthNormalized=1&VideoLayer.2.PositionNormalized.1=0.3&VideoLayer.2.PositionNormalized.2=1.0&BlendList.1=RV01&BlendList.2=RV02&MixList.1=RV01&MixList.2=RV02&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "LayoutId": "21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 特殊错误码 {#section_ecx_slh_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidVideoLayersAndBlendListSize.Mismatch|Specified parameter VideoLayers and BlendList size is invalid.|400|VideoLayers 与BlendList 元素数量不符|
|InvalidVideoLayersAndBlendListSize.Mismatch|Specified parameter AudioLayers and MixList size is invalid.|400|AudioLayers 与MixList 元素数量不符|
|InvalidPositionNormalized.Malformed|Specified parameter PositionNormalized size should be 2 is invalid.|400|位置数组元素数量为2|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

