# DescribeLiveStreamRecordContent {#reference2389 .reference}

查询录制内容。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamRecordContent|系统规定参数。取值：DescribeLiveStreamRecordContent|
|AppName|String|是|testApp|直播流所属应用名称。|
|DomainName|String|是|www.yourdomain.com|您的加速域名。|
|EndTime|String|是|2017-12-22T08:00:00:00Z| 结束时间。

 -   格式：UTC时间。
-   示例：2015-12-01T17:36:00Z。
-   与 StartTime 的间隔时间不能超过 4 天。

 |
|StartTime|String|是|2017-12-21T08:00:00:00Z| 开始时间。

 格式：UTC时间。

 示例：2015-12-01T17:36:00Z。

 |
|StreamName|String|是|testStream|直播流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RecordContentInfoList| | |录制内容列表。|
|  └OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OSS endpoint。|
|  └OssBucket|String|test123|OSS 存储 bucket 名称。|
|  └OssObjectPrefix|String|record/\{Date\}/\{UnixTimestamp\}\_\{Sequence\}|OSS 存储的录制文件名的规则。|
|  └StartTime|String|2015-12-01T17:36:00Z| 开始时间。

 格式：2015-12-01T17:36:00Z。

 |
|  └EndTime|String|2015-12-01T17:36:00Z| 结束时间。

 格式：2015-12-01T17:36:00Z。

 |
|  └Duration|Float|10|录制时长。|
|RequestId|String|62136AE6-7793-45ED-B14A-60D19A9486D3|该条任务请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com/?Action=DescribeLiveStreamRecordContent&DomainName=live.aliyunlive.com&AppName=aliyuntest&StreamName=xxx&StartTime=xxx&EndTime=xxx&<公共请求参数> 
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "RecordContentInfoList":{
        "RecordContentInfo":[{
            "Duration":14638.0,
            "EndTime":"2016-05-25T09:41:09Z",
            "OssBucket":"livevideo-test",
            "OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
            "OssObjectPrefix":"record/{Date}/{UnixTimestamp}_{Sequence}",
            "StartTime":"2016-05-25T05:37:11Z"
        }]
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

## 错误码 {#section_vsc_5fc_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

