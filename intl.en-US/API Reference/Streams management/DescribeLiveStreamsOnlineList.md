# DescribeLiveStreamsOnlineList {#concept_35409_zh .concept}

View the information of all the streams being pushed under a specific domain name \(or an app under a specified domain name\).

**Note:** The access frequency of DescribeLiveStreamsOnlineList is limited to 1,000 times per minute. We recommend that you do not call it frequently, so as not to cause the business to be unavailable.

## Request parameters {#section_k4f_qm1_dfb .section}

|Parameters|Type|Required|Example values|Description|
|:---------|:---|:-------|:-------------|:----------|
|Action|String|Yes|DescribeLiveStreamsOnlineList|The name of this interface. Value: Value: DescribeLiveStreamsOnlineList|
|DomainName|String|Yes|play.yourdomain.com|Your Live domain name.|
|AppName|String|No|testApp|Name of the app.**Note:** AppName does not support wildcard query \(\*\) and fuzzy query.

|
|StreamName|String|No|livestream|Stream name.**Note:** StreamName does not support wildcard \(\*\) queries, but supports fuzzy queries.

|
|StreamType|String|No|all|Stream type. Valid values:

-   all
-   raw
-   trans

Correspondingly check all the streams, raw streams and transcoding streams. Default: all means returing all ll the stream information.|
|QueryType|String|No|fuzzy|Specifies whether the stream name is fuzzy matching.Value:

-   fuzzy: fuzzy matching
-   strict: precise matching

|
|StartTime|String|No|2016-06-29T19:00:00Z|Start time.-   UTC format
-   Example: 2016-06-29T19:00:00Z

|
|EndTime|String|No|2016-06-30T19:00:00Z|EndTime.-   UTC format
-   Example: 2016-06-30T19:00:00Z
-   The interval between EndTime and StartTime cannot exceed 30 days.

|
|PageNum|Integer|No|1|The page number. Default value: 1.|
|PageSize|Integer|No|1,500| Size of each page. Maximum value: 3000.

 Value: Any integer between 1 and 3000.

 Default value: 2000

 |

## Response parameters {#section_p4f_qm1_dfb .section}

|Parameters|Type|Example values|Description|
|:---------|:---|:-------------|:----------|
|OnlineInfo| | |Information of the stream being pushed.|
|  └DomainName|String|play.yourdomain.com|The Live domain name, which the stream belongs to.|
|  └AppName|String|AppName|Name of the app, which the stream belongs to.|
|  └StreamName|String|StreamName|Name of the stream.|
|  └PublishTime|String|2015-12-02T06:58:04Z|The time when stream ingest starts in UTC.|
|  └PublishUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|The full ingest URL.|
|  └PublishDomain|String|push.aliyunlive.com|The ingest domain. If using the live center ingest, you can enter the streaming domain directly.|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|The ID of the job request.|
|PageNum|Integer|1|The page number.|
|PageSize|Integer|10|The page size.|
|TotalNum|Integer|10|The total number that comforms with the conditions.|
|TotalPage|Integer|100|The total number of pages.|

## Example {#section_zcx_4j1_dfb .section}

Request example

```
https://live.aliyuncs.com/?Action=DescribeLiveStreamsOnlineList&DomainName=test101.aliyunlive.com&PageSize=10&PageNum=2&<Public Request Parameter> 
```

**Note:** For more information, see [Public Request Parameter](reseller.en-US/API Reference/APIs invoke/Public parameters.md#).

Normal response example

JSON format

```
{
    "OnlineInfo":{
        "LiveStreamOnlineInfo":[{
            "AppName":"xchen",
            "DomainName":"test101.cdnpe.com",
            "PublishTime":"2015-12-02T06:58:04Z",
            "PublishUrl":"rtmp://test101.cdnpe.com/xchen",
            "StreamName":"testxchen"
        }]
    },
    "PageNum":2,
    "PageSize":10,
    "RequestId":"0D70427D-91E4-4349-AAD3-5511A5BB823B",
    "TotalNum":11,
    "TotalPage":2
}
```

Exception response example

JSON format

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## Error code {#section_v4f_qm1_dfb .section}

For more information about error code of this product, see Error code.

