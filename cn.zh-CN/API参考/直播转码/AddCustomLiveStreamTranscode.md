# AddCustomLiveStreamTranscode {#concept_66944_zh .concept}

添加自定义转码配置信息。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AddCustomLiveStreamTranscode|系统规定参数。取值：AddCustomLiveStreamTranscode|
|App|String|是|AppName| 直播流所属应用名称。

 取值要求： 数字、大小写字母、下划线\("\_"\)或短横线\("-"\)。

 |
|Domain|String|是|live.aliyunlive.com|您的加速域名。|
|FPS|Integer|是|30| 转码视频帧率。单位：fps。

 取值范围：\[1, 30\]

 |
|Height|Integer|是|720| 转码视频宽度。

 -   取值范围：Width ≥ 100
-   max\(Height, Width\) ≤ 1920
-   min\(Height, Width\) ≤ 1080

 |
|Template|String|是|LDtest| 转码模板自定义名称。

 取值要求：数字、大小写字母或短横线\("-"\)。

**说明：** 不能与标准的转码模板命名重复。

 |
|TemplateType|String|是|h264| 自定义转码模版类型。目前支持：

 -   h264 \(自定义H264标准模版\)
-   h264-nbhd \(自定义H264窄带高清TM模版\)

 |
|VideoBitrate|Integer|是|720| 转码视频比特率。单位：kbps。

 取值范围：\[1，6000\]

**说明：** 转码视频会尽量接近您所设定的比特率, 但转码视频的实际比特率不能保证和您所设定的完全一致, 尤其是当您设定的比特率过大或过小时。

 |
|Width|Integer|是|576| 转码视频宽度。

 -   取值要求：Width ≥ 100
-   max\(Height, Width\) ≤ 1920
-   min\(Height, Width\) ≤ 1080

 |
|Version|String|否|1.0|版本号|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|该请求Id|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=AddCustomLiveStreamTranscode&Domain=test101.cdnpe.com&App=AppName&Template=LDtest&TemplateType=h264&Height=1280&Width=720&FPS=25&VideoBitrate=2400&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

