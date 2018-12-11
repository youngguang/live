# DescribeLivePullStreamConfig {#concept_57733_zh .concept}

查询域名下拉流配置信息。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLivePullStreamConfig|系统规定参数。取值：DescribeLivePullStreamConfig|
|DomainName|String|是|play.yourdomain.com|您的拉流域名。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|LiveAppRecordList| | |拉流配置。|
|  └DomainName|String|play.yourdomain.com|流所属拉流域名。|
|  └AppName|String|AppName|直播流所属应用名称。|
|  └StreamName|String|StreamName|流名称。|
|  └SourceUrl|String|play.yourdomain.com|拉流源站。|
|  └StartTime|String|2016-05-15T01:30:00Z|开始时间。|
|  └EndTime|String|2016-05-20T01:33:00Z|结束时间。|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=DescribeLivePullStreamConfig&DomainName=test101.aliyunlive.com&<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数。](cn.zh-CN/API参考/调用方式/公共参数.md#)

正常返回示例

JSON格式

```
{
    "LiveAppRecordList":{
        "LiveAppRecord":[{
            "AppName":"xxxx",
            "DomainName":"live.aliyunlive.com",
            "EndTime":"2016-05-20T01:33:00Z",
            "SourceUrl":"http://test",
            "StartTime":"2016-05-15T01:30:00Z",
            "StreamName":"xxxxxx"
        }]
    },
    "RequestId":"A3136B58-5876-4168-83CA-B562781981A0"
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

