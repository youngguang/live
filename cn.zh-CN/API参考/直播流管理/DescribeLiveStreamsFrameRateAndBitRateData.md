# DescribeLiveStreamsFrameRateAndBitRateData {#concept_60410_zh .concept}

实时查询直播流帧率和码率数据。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamsFrameRateAndBitRateData|系统规定参数。取值：DescribeLiveStreamsFrameRateAndBitRateData|
|DomainName|String|是|www.yourdomain.com|您的域名。|
|AppName|String|是|testApp|直播流所属应用名称。|
|EndTime|String|否|2017-12-21T08:00:00:00Z| 结束时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在7天内，且EndTime超过当前时间。

 |
|StartTime|String|否|2017-12-21T08:00:00:00Z| 开始时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在7天内，且EndTime超过当前时间。

 |
|StreamName|String|否|testStream|直播流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|FrameRateAndBitRateInfos| | |各直播流的帧率/码率信息。|
|  └StreamUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|直播流的URL。|
|  └VideoFrameRate|Float|30|直播流的视频帧率。|
|  └AudioFrameRate|Float|50|直播流的音频帧率。|
|  └BitRate|Float|600|直播流的码率。|
|  └Time|String|2016-09-13T16:05:00Z| 统计时刻。

 UTC时间。

 |
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeLiveStreamsFrameRateAndBitRateData&DomainName=live.aliyunlive.com&<公共请求参数> 
```

正常返回示例

JSON格式

```
{
    "FrameRateAndBitRateInfos":{
        "FrameRateAndBitRateInfo":[{
            "AudioFrameRate":"167.67",
            "BitRate":"192.02",
            "StreamUrl":"rtmp://live.aliyunlive.com/live/test101",
            "Time":"2016 - 09 - 13 T16: 05: 00 Z",
            "VideoFrameRate":"30.01"
        }]
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

