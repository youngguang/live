# DescribeLiveStreamRecordIndexFile {#reference2902 .reference}

查询单个录制索引文件。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamRecordIndexFile|系统规定参数。取值：DescribeLiveStreamRecordIndexFile|
|AppName|String|是|testApp|直播流所属应用名称。|
|DomainName|String|是|www.yourdomain.com|您的加速域名。|
|RecordId|String|是|xxx|索引文件 ID。|
|StreamName|String|是|testStream|直播流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|5EBF2AC3-4B73-40A5-8B32-83F49D5F035E|请求ID。|
|RecordIndexInfo| | |录制配置。|
|  └RecordUrl|String|[http://xxx.xxx/atestObject.m3u8](http://xxx.xxx/atestObject.m3u8)|索引文件地址。|
|  └DomainName|String|test.com|流所属加速域名。|
|  └AppName|String|xxx|流所属应用名称。|
|  └StreamName|String|xxx|直播流名称。|
|  └OssBucket|String|tes123|OSS 存储的 bucket 名称。|
|  └OssEndpoint|String|oss-cn-hangzhou.aliyuncs.com|OSS 存储的 endpoint 名称。|
|  └OssObject|String|test123|OSS 存储的录制文件名。|
|  └StartTime|String|2015-12-01T17:36:00Z| 开始时间。

 格式：2015-12-01T17:36:00Z。

 |
|  └EndTime|String|2016-05-25T05:47:11Z| 结束时间。

 格式：2015-12-01T17:36:00Z。

 |
|  └Duration|Float|588.849|录制时长。|
|  └Height|Integer|480|视频高。|
|  └Width|Integer|640|视频宽。|
|  └CreateTime|String|2016-05-27T09:40:56Z|创建时间。|
|  └RecordId|String|c4d7f0a4-b506-43f9-8de3-07732c3f3d82|索引文件 ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=DescribeLiveStreamRecordIndexFile&DomainName=live.aliyunlive.com&AppName=aliyuntest&StreamName=xxx&RecordId=xxx&<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "RecordIndexInfo":{
        "AppName":"xxx",
        "CreateTime":"2016-05-27T09:40:56Z",
        "DomainName":"xxx",
        "Duration":588.849,
        "EndTime":"2016-05-25T05:47:11Z",
        "Height":480,
        "OssBucket":"bucket",
        "OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
        "OssObject":"atestObject.m3u8",
        "RecordId":"c4d7f0a4-b506-43f9-8de3-07732c3f3d82",
        "RecordUrl":"http://xxx.xxx/atestObject.m3u8",
        "StartTime":"2016-05-25T05:37:11Z",
        "StreamName":"xxx",
        "Width":640
    },
    "RequestId":"5EBF2AC3-4B73-40A5-8B32-83F49D5F035E"
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

## 错误码 {#section_wsn_bhc_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

