# DescribeLiveStreamTranscodeInfo {#concept_45048_zh .concept}

查询转码配置信息。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamTranscodeInfo|系统规定参数。取值：DescribeLiveStreamTranscodeInfo|
|DomainTranscodeName|String|是|play.aliyunlive.com|您的加速域名。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|DomainTranscodeList| | |转码配置信息。|
|  └TranscodeName|String|play.aliyunlive.com|播放域名。|
|  └TranscodeApp|String|app|应用名称。|
|  └TranscodeTemplate|String|lld| 转码模版。目前有：

 -   标准质量模板：lld、lsd、lhd、lud。
-   高品质（窄带高清TM转码）模板：ld、sd、hd、ud。

 |
|  └CustomTranscodeParameters| | |用户自定义转码配置。|
|    └VideoBitrate|Integer|3000|转码视频比特率。单位：kbps|
|    └FPS|Integer|15|转码视频帧率。单位：fps|
|    └Height|Integer|1200|转码视频高度。|
|    └Width|Integer|1000|转码视频宽度。|
|    └TemplateType|String|h264|自定义转码模版类型。|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求 ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=DescribeLiveStreamTranscodeInfo&DomainTranscodeName=xxxxx&<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "DomainTranscodeList":{
        "DomainTranscodeInfo":[
            {
                "TranscodeApp":"xxxx",
                "TranscodeName":"xxxx",
                "TranscodeTemplate":"xxxx"
            },
            {
                "CustomTranscodeParameters":{
                    "FPS":25,
                    "Height":720,
                    "Type":"h264",
                    "VideoBitrate":2000,
                    "Width":1280
                },
                "TranscodeApp":"yyyy",
                "TranscodeName":"yyyy",
                "TranscodeTemplate":"yyyy"
            }
        ]
    },
    "RequestId":"62136AE6-7793-45ED-B14A-60D19A9486D3"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

