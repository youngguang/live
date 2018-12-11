# DescribeLiveDomainTranscodeData {#reference2392 .reference}

查询直播域名转码时长数据。

-   支持用户查询单个直播域名在指定时间区段内的每日转码时长数据。

-   每日转码时长数据包括：当日转码总时长和区分转码规格的时长数据列表。

-   支持查询 2018/01/01 起的数据，数据查询的起止时间跨度最大为90天。


## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveDomainTranscodeData|系统规定参数。取值：DescribeLiveDomainTranscodeData|
|DomainName|String|是|www.example.com|需要查询的直播域名。|
|StartTime|String|是|2018-01-01T00:00:00Z| 获取数据起始时间点。

 -   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式：YYYY-MM-DDThh:mm:ssZ。
-   支持查询2018/01/01起的数据，即 StartTime ≥ 2018-01-01T00:00:00Z。

 |
|EndTime|String|是|2018-01-02T01:00:00Z| 获取数据结束时间。

 -   需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式：YYYY-MM-DDThh:mm:ssZ。

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|TranscodeDataInfos| | |直播转码时长的每日数据统计。|
|  └Date|String|20180202|日期，具体到天。|
|  └Total|Integer|4710| 单日转码总时长。

 单位：秒。

 |
|  └Detail|String|\{ “LD\_CASTER”: 86315, “SD\_CASTER”: 86315 \}, “Date”: “20180212”, “Total”: 172630\}|区分转码规格的转码时长信息。|
|RequestId|String|B955107D-E658-4E77-B913-E0AC3D31693F|请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
/?Action=DescribeLiveDomainTranscodeData
&DomainName=www.example.com
&EndTime=2018-02-12T00:00:00Z
&StartTime=2018-02-15T00:00:00Z
&<公共请求参数> 
```

正常返回示例

JSON格式

```
{
    "RequestId":"BCB009C1-10B1-47F0-BD2F-936D5DD4F5FA",
    "TranscodeDataInfos":{
        "TranscodeDataInfo":[
            {
                "Date":"20180212",
                "Detail":{
                    "LD_CASTER":86315,
                    "SD_CASTER":86315
                },
                "Total":172630
            },
            {
                "Date":"20180213",
                "Detail":{
                    "LD_CASTER":86315,
                    "SD_CASTER":86320
                },
                "Total":172635
            },
            {
                "Date":"20180214",
                "Detail":{
                    "LD_CASTER":86315,
                    "SD_CASTER":86315
                },
                "Total":172630
            },
            {
                "Date":"20180215",
                "Detail":{
                    "LD_CASTER":86315,
                    "SD_CASTER":86320
                },
                "Total":172635
            }
        ]
    }
}
```

异常返回示例

JSON格式

```
{
    "Code":"InvalidEndTime.BeyondCurrent",
    "HostId":"live.aliyuncs.com",
    "Message":"EndTime beyond current time.",
    "RequestId":"D561201C-1192-4BCB-BDA9-AD16AA62F6FD"
}
```

## 错误码 { .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

