# DescribeRoomList {#reference_ysf_d11_mfb .reference}

获取房间列表，创建直播间后可获取。

## 请求参数 {#section_nsv_h11_mfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRoomList|
|AppId|String|是|业务方APP ID。|
|RoomStatus|int|否|状态。-   0：流关闭，
-   1：流开启，
-   2：流中断。

|
|Order|String|否|排序方式。默认：desc 降序

|
|PageNum|int|否|页码。默认：1

|
|PageSize|int|否|每页数量。默认：10

|

## 返回参数 {#section_rdg_n11_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|TotalNum|int|总条数|
|TotalPage|int|总页数|
|RoomList|JsonArray|房间列表|

**Room**

|参数|类型|描述|
|:-|:-|:-|
|RoomId|String|房间ID。|
|AnchorId|String|房间主人ID。|
|RoomStatus|int|状态。-   0：流关闭，
-   1：流开启，
-   2：流中断。

|
|CreateTime|String|创建时间。格式：yyyy-MM-dd’T’HH:mm:ss’Z’

|

## 示例 {#section_jqv_f11_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeRoomList&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"TotalPage": 1,
"TotalNum": 2,
"RequestId": "EB8B1220-9B1D-4B1E-A7F8-F02E872BBA2C",
"RoomList": {
"Room": [
{
"Status": 0,
"AnchorId": "c8624b97b7b54acba4b65951c12d3c5b",
"RoomId": "ewynykkf3nftbzqo",
"CreateTime": "2018-05-25T03:00:08Z"
},
{
"Status": 0,
"AnchorId": "2f078371-d06e-40d5-8dee-d1c6149afa1e",
"RoomId": "hello_wxg_room",
"CreateTime": "2018-05-24T08:58:26Z"
}
]
}
}
```

## 特殊错误码 {#section_g5h_fb1_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

