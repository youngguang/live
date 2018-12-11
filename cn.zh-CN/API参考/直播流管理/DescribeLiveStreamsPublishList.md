# DescribeLiveStreamsPublishList {#concept_35408_zh .concept}

获取某一时间段内某个域名（或域名下某应用或某个流）的推流记录。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamsPublishList|系统规定参数。取值：DescribeLiveStreamsPublishList|
|DomainName|String|是|play.yourdomain.com|您的域名。|
|EndTime|String|是|2017-12-22T08:00:00:00Z| 结束时间。

 -   UTC 格式，例如：2016-06-30T19:00:00Z。
-   EndTime 和 StartTime 之间的间隔不能超过 30 天。

 |
|StartTime|String|是|2017-12-21T08:00:00:00Z| 起始时间。

 UTC 格式，例如：2016-06-29T19:00:00Z。

 |
|AppName|String|否|testApp|直播流所属应用名称。**说明：** AppName 不支持通配符（\*）查询，且不支持模糊查询。

|
|PageNumber|Integer|否|1| 取得第几页。

 默认值：1

 |
|PageSize|Integer|否|1500|分页大小。

-   最大值：3000。
-   取值范围：1~3000 之前的任意整数。

默认值：3000|
|StreamName|String|否|testStream|直播流名称。**说明：** StreamName不支持通配符（\*）查询，但支持模糊查询 。

|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|PublishInfo| | |推流记录信息。|
|  └DomainName|String|play.yourdomain.com|流所属加速域名。|
|  └AppName|String|AppName|流所属应用名称。|
|  └StreamName|String|StreamName|直播流名称。|
|  └StreamUrl|String|[http://play.aliyunlive.com/AppName/StreamName.flv](http://play.aliyunlive.com/AppName/StreamName.flv)|直播流的 URL。|
|  └PublishTime|String|2015-12-02T03:05:53Z| 开始推流时刻。

 UTC 时间。

 |
|  └StopTime|String|2015-12-02T03:11:19Z| 停止推流时刻。

 UTC 时间。

 |
|  └ClientAddr|String|10.175.60.33|主播 IP。|
|  └EdgeNodeAddr|String|10.175.30.21|CDN 上行节点 IP。|
|  └PublishUrl|String|rtmp://push.aliyunlive.com/AppName/StreamName|推流完整URL地址。|
|  └PublishDomain|String|play.yourdomain.com|推流域名。|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|
|PageNum|Integer|2|分页的页码。|
|PageSize|Integer|10|每页大小。|
|TotalNum|Integer|11|符合条件的总个数。|
|TotalPage|Integer|2|总页数。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeLiveStreamsPublishList&DomainName=test101.aliyunlive.com&StartTime=2015-06-25T03:30:50Z&EndTime=2015-12-26T03:30:50Z&PageSize=10&PageNum=2&<公共请求参数> 
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "PageNum":2,
    "PageSize":10,
    "PublishInfo":{
        "LiveStreamPublishInfo":[{
            "AppName":"xchen",
            "ClientAddr":"10.175.60.33",
            "DomainName":"test101.cdnpe.com",
            "EdgeNodeAddr":"10.175.30.21",
            "PublishDomain":"test101.cdnpe.com",
            "PublishTime":"2015-12-02T03:05:53Z",
            "PublishUrl":"rtmp://test101.cdnpe.com/xchen",
            "StopTime":"2015-12-02T03:11:19Z",
            "StreamName":"testxchen",
            "StreamUrl":"rtmp://xxx/xxxx"
        }]
    },
    "RequestId":"1C0E0C22-77B7-42AC-8212-AF99B2E0077F",
    "TotalNum":11,
    "TotalPage":2
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

