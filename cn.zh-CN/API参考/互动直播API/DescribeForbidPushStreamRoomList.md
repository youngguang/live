# DescribeForbidPushStreamRoomList {#reference_ddf_kb1_mfb .reference}

获取禁播房间列表，被禁止推流的房间可以通过此接口获取。

## 请求参数 {#section_osl_mb1_mfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeForbidPushStreamRoomList|
|AppId|String|是|控制台创建应用所获取的AppID。|
|Order|String|否|排序方式。默认：desc 降序

|
|PageNum|int|否|页码。默认：1

|
|PageSize|int|否|每页数量。默认：10

|

## 返回参数 {#section_g35_qb1_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|TotalNum|int|总条数|
|TotalPage|int|总页数|
|RoomList|JsonArray|房间列表|

**Room**

|参数|类型|描述|
|:-|:-|:-|
|RoomId|String|房间Id|
|AnchorId|String|主播Id|
|OpStartTime|String|禁播开始时间\(UTC\)|
|OpEndTime|String|禁播结束时间\(UTC\)|

## 示例 {#section_uw1_mb1_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeForbidRooms&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"TotalPage": 1,
"TotalNum": 3,
"RequestId": "89867394-E4C7-4612-A467-C20F062B0C07",
"RoomList": {
"Room": [
{
"AnchorId": "",
"RoomId": "miyou_test_1",
"OpStartTime": "2018-05-24T08:58:26Z",
"OpEndTime": "2018-05-24T08:58:26Z"
},
{
"AnchorId": "",
"RoomId": "roomId-1000",
"OpStartTime": "2018-05-24T08:58:26Z",
"OpEndTime": "2018-05-24T08:58:26Z"
},
{
"AnchorId": "",
"RoomId": "roomId-1001",
"OpStartTime": "2018-05-24T08:58:26Z",
"OpEndTime": "2018-05-24T08:58:26Z"
}
]
}
}
```

## 特殊错误码 {#section_tz3_pc1_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

