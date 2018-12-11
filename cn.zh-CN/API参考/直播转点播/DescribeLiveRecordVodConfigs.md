# DescribeLiveRecordVodConfigs {#concept_63970_zh .concept}

查询直转点配置列表。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveRecordVodConfigs|系统规定参数。取值：DescribeLiveRecordVodConfigs|
|DomainName|String|是|play.aliyunlive.com|您的加速域名。|
|AccessKeyId|String|否|LTAIJUJDeDini0dd|阿里云颁发给用户的访问服务所用的密钥ID。|
|AppName|String|否|app|直播流所属应用名称。|
|PageNum|Long|否|1| 分页的页码。

 默认值：1

 |
|PageSize|Long|否|10| 每页大小。

-   取值范围：\[5，100\]
-   默认值：10

 |
|StreamName|String|否|stream|直播流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|rtmp://play.aliyunlive.com/AppName/StreamName|该条任务请求ID|
|PageNum|Integer|1|分页页码。|
|PageSize|Integer|1|页大小。|
|Total|String|3|总页数。|
|LiveRecordVodConfigs| | |配置信息列表。|
|  └CreateTime|String|2015-12-01T17:37:00Z| 创建时间。

 -   UTC 时间。
-   格式：2015-12-01T17:37:00Z。

 |
|  └DomainName|String|play.aliyunlive.com|流所属加速域名。|
|  └AppName|String|app|流所属应用名称。|
|  └StreamName|String|stream|直播流名称。|
|  └VodTranscodeGroupId|String|e2d796d3bb5fd8049d32bff62f940711|点播转码组模板ID。|
|  └CycleDuration|Integer|360| 周期录制时长。

-   单位：秒。
-   取值范围：\[300，21600\]
-   默认值：3600秒

 |

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DescribeLiveRecordVodConfigs&DomainName=live.aliyunlive.com<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "LiveRecordVodConfigs":[{
        "AppName":"aliyuntest",
        "CycleDuration":300,
        "DomainName":"xxxxx",
        "VodTranscodeGroupId":"xxxx"
    }],
    "PageNum":5,
    "PageSize":10,
    "RequestId":"5056369B-D337-499E-B8B7-B761BD37B08A",
    "Total":100
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

