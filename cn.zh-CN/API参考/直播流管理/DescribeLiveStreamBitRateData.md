# DescribeLiveStreamBitRateData {#concept_35424_zh .concept}

查询rtmp协议的直播流的设置时间范围内的一组帧率和码率，适用于获取历史数据。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamBitRateData|系统规定参数。取值：DescribeLiveStreamBitRateData|
|DomainName|String|是|www.yourdomain.com|您的域名。|
|AppName|String|否|testApp|直播流所属应用名称。|
|EndTime|String|否|2017-12-22T08:00:00Z| 结束时间。

 -   UTC格式，例如：2016-06-30T19:00:00Z

 |
|StartTime|String|否|2017-12-21T08:00:00Z| 起始时间。

 -   UTC格式，例如：2016-06-29T19:00:00Z。

 |
|StreamName|String|否|testStream|直播流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|FrameRateAndBitRateInfos| | |各直播流的帧率/码率信息。|
|  └StreamUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|直播流的 URL。|
|  └VideoFrameRate|Float|30|直播流的视频帧率。|
|  └AudioFrameRate|Float|100|直播流的音频帧率。|
|  └BitRate|Float|600|直播流的码率。|
|  └Time|String|2016-09-13T16:04:00Z| 统计时刻。

 UTC 时间。

 |
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=DescribeLiveStreamsFrameRateAndBitRateData&DomainName=live.aliyunlive.com&AppName=testApp&StreamName=testStream&StartTime=2016-09-13T16:00:00Z&EndTime=2016-09-13T16:05:00Z&<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "FrameRateAndBitRateInfos":{
        "FrameRateAndBitRateInfo":[
            {
                "AudioFrameRate":"167.67",
                "BitRate":"192.02",
                "StreamUrl":"rtmp://live.aliyunlive.com/live/test101",
                "Time":" 2016 - 09 - 13 T16: 05: 00 Z",
                "VideoFrameRate":"30.01"
            },
            {
                "AudioFrameRate":"165.43",
                "BitRate":"192",
                "StreamUrl":"rtmp://live.aliyunlive.com/live/test102",
                "Time":"2016 - 09 - 13 T16: 04: 00 Z",
                "VideoFrameRate":"29.22"
            },
            {
                "AudioFrameRate":"166.77",
                "BitRate":"192",
                "StreamUrl":"rtmp://live.aliyunlive.com/live/test103",
                "Time":"2016 - 09 - 13 T16: 03: 00 Z",
                "VideoFrameRate":"30.33"
            },
            {
                "AudioFrameRate":"167.53",
                "BitRate":"192",
                "StreamUrl":"rtmp://live.aliyunlive.com/live/test104",
                "Time":"2016 - 09 - 13 T16: 02: 00 Z",
                "VideoFrameRate":"30"
            },
            {
                "AudioFrameRate":"168.01",
                "BitRate":"192",
                "StreamUrl":"rtmp://live.aliyunlive.com/live/test104",
                "Time":"2016 - 09 - 13 T16: 01: 00 Z",
                "VideoFrameRate":"30"
            }
        ]
    },
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
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

