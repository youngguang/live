# DescribeCasterLayouts {#reference4109 .reference}

查询布局列表。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterLayouts|
|CasterId|String|是|导播台Id|
|LayoutId|String|否|布局Id，若未指定，则查询导播台下所有布局列表|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|Layouts|\[\]Layout|布局列表|

Layout

|名称|类型|描述|
|:-|:-|:-|
|LayoutId|String|布局Id|
|VideoLayers|\[\]VideoLayer|videolayer配置列表，采用数组默认序列|
|AudioLayers|\[\]AudioLayer|Audiolayer配置列表|
|BlendList|\[\]String|位置关联列表，与VideoLayers顺序保持一致|
|MixList|\[\]String|位置关联列表，与AudioLayers顺序保持一致|

VideoLayer

|名称|类型|描述|
|:-|:-|:-|
|FillMode|String|元素填充方式。-   不填充：”none”
-   自适应：”fit”
-   默认：不填充。
-   若采用不填充模式，则以画面作为配置目标进行Layer设置。
-   若采用自适应模式，则以填充区（框）作为配置目标进行Layer设置，此时画面会按照原始的宽高比缩放，长边对齐的自适应方式在填充区（框）内居中填充，若填充区宽高比和画面不一致，则短边两侧无填充（显示为下层Layer画面，若下层未配置Layer，默认为底图黑色）。

|
|HeightNormalized|Float|设置该layer元素的高度归一化比例值。-   若采用不填充模式，元素的宽度会按照该高度来进行等比缩放，默认值：0，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式，该字段必输且大于0，表示填充区\(框\)高度归一化比例值。

|
|WidthNormalized|Float|设置该layer元素的宽度归一化比例值。-   若采用不填充模式，元素的高度会按照该宽度来进行等比缩放，默认值：0，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式，该字段必输且大于0，表示填充区\(框\)宽度归一化比例值。

|
|PositionNormalized|\[\]Float|设置该layer 元素的位置归一化值\[x，y\]。默认为：\[0，0\]

**说明：** x，y需要进行归一化计算。

 |
|PositionRefer|String|设置元素的position 参考坐标值。-   取值范围：”topLeft”、”topRight”、”bottomLeft”、”bottomRight”以及”center”、”topCenter”、”bottomCenter”、”leftCenter”、”rightCenter”
-   默认值：”topLeft”

|
|FixedDelayDuration|Integer|该字段对视频进行固定延迟设置，可用于字幕同步。-   单位：ms
-   默认值：0
-   取值范围：\[0-5000\]

 |

AudioLayer

|名称|类型|描述|
|:-|:-|:-|
|VolumeRate|Float|设置该layer元素的高度归一化比例值，其中元素的宽度会按照该高度来进行等比缩放。默认值：0，表示按照元素的原始尺寸进行显示。

|
|ValidChannel|String|确定哪些声道可以作为音量输入。-   取值范围：”leftChannel”、”rightChannel”、”all”
-   默认值：”all”

|
|FixedDelayDuration|Integer|该字段对视频进行固定延迟设置，可用于字幕同步。-   单位：ms
-   默认值：0
-   取值范围：\[0-5000\]

|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DescribeCasterLayouts&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&<公共请求参数>
}
```

返回示例

```
{
    "RequestId": "3be7ade8-d907-483c-b24a-0dad4595beaf",
    "Layouts": [
        {
            "MixList": [
                "RV01"
            ],
            "AudioLayers": [
                {
                    "ValidChannel": "all",
                    "VolumeRate": 1
                }
            ],
            "VideoLayers": [
                {
                    "HeightNormalized": 0.5,
                    "PositionRefer": "topLeft",
                    "WidthNormalized": 0.5,
                    "PositionNormalized": [
                        0,
                        0.3
                    ]
                },
                {
                    "HeightNormalized": 0.5,
                    "PositionRefer": "topLeft",
                    "WidthNormalized": 0.5,
                    "PositionNormalized": [
                        0.5,
                        0.3
                    ]
                }
            ],
            "LayoutId": "72d2ec7a-4cd7-4a01-974b-7cd53947f053",
            "BlendList": [
                "RV01",
                "RV02"
            ]
        },
        {
            "MixList": [
                "RV01"
            ],
            "AudioLayers": [
                {
                    "ValidChannel": "all",
                    "VolumeRate": 0.5
                }
            ],
            "VideoLayers": [
                {
                    "HeightNormalized": 1,
                    "PositionRefer": "topLeft",
                    "WidthNormalized": 1,
                    "PositionNormalized": [
                        0,
                        0
                    ]
                },
                {
                    "HeightNormalized": 0.4,
                    "PositionRefer": "topLeft",
                    "WidthNormalized": 0.4,
                    "PositionNormalized": [
                        0.1,
                        0.1
                    ]
                }
            ],
            "LayoutId": "21926b36-7dd2-4fde-ae25-51b5bc8e52d8",
            "BlendList": [
                "RV01",
                "RV02"
            ]
        }
    ]
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404| |
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

