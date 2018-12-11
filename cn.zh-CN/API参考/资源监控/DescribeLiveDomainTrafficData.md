# DescribeLiveDomainTrafficData {#reference2805 .reference}

查询直播域名网络流量监控数据，单位：byte。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。

-   支持批量域名查询，多个域名用逗号（半角）分隔。

-   最多可获取最近90天的数据。


## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveDomainTrafficData|系统规定参数。取值：DescribeLiveDomainTrafficData|
|DomainName|String|否|test.com| 需要查询的直播域名。

 -   若参数为空，默认返回所有直播域名合并后数据。
-   支持批量域名查询。
-   多个域名用逗号（半角）分隔。

 |
|StartTime|String|否|2017-12-10T20:00:00Z| 获取数据起始时间点。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为5分钟。
-   最大数据粒度为1天。
-   最长可查询45天内的数据。

 |
|EndTime|String|否|2017-12-10T21:00:00Z| 结束时间需大于起始时间。

 -   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为5分钟。
-   最大数据粒度为1天。
-   最长可查询45天内的数据。

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|DomainName|String|test.com|直播域名信息。|
|DataInterval|String|300|查询数据的时间粒度。|
|TrafficDataPerInterval| | |每个时间间隔的流量数据。|
|  └TimeStamp|String|2017-12-10T20:00:05Z|时间片起始时刻。|
|  └TrafficValue|String|454680793|总流量。|
|  └HttpTrafficValue|String|0|http流量。|
|  └HttpsTrafficValue|String|454680793|https流量。|
|RequestId|String|B955107D-E658-4E77-B913-E0AC3D31693E|请求ID。|
|StartTime|String|2017-12-10T20:00:00Z|开始时间。|
|EndTime|String|2017-12-10T21:00:00Z|结束时间。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 http://live.aliyuncs.com?Action=DescribeLiveDomainTrafficData&DomainName=test.com
&StartTime=2017-12-10T20:00:00Z
&EndTime=2017-12-10T21:00:00Z
&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "DataInterval":"300",
    "DomainName":"test.com",
    "EndTime":"2017-12-10T21:00:00Z",
    "RequestId":"B955107D-E658-4E77-B913-E0AC3D31693E",
    "StartTime":"2017-12-10T20:00:00Z",
    "TrafficDataPerInterval":{
        "DataModule":[
            {
                "HttpTrafficValue":"0",
                "HttpsTrafficValue":"423304182",
                "TimeStamp":"2017-12-10T20:00:00Z",
                "TrafficValue":"423304182"
            },
            {
                "HttpTrafficValue":"0",
                "HttpsTrafficValue":"454680793",
                "TimeStamp":"2017-12-10T20:00:05Z",
                "TrafficValue":"454680793"
            }
        ]
    }
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

## 错误码 { .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

