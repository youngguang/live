# DescribeRoomKickoutUserList {#reference_uct_tc1_mfb .reference}

获取房间内被踢出用户列表，踢人操作在客户端上发起。

## 请求参数 {#section_rmc_yc1_mfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRoomKickoutUserList|
|AppId|String|是|控制台创建应用所获取的AppID。|
|RoomId|String|是|房间号，最多16位字符。|
|Order|String|否|排序方式。默认：desc 降序

|
|PageNum|int|否|页码。默认：1

|
|PageSize|int|否|每页数量。默认：10

|

## 返回参数 {#section_yhh_1d1_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|TotalNum|int|总条数|
|TotalPage|int|总页数|
|UserList|JsonArray|用户列表|

**User**

|参数|类型|描述|
|:-|:-|:-|
|AppUid|String|三方用户ID|
|OpStartTime|String|踢出开始时间\(UTC\)|
|OpEndTime|String|踢出结束时间\(UTC\)|

## 示例 {#section_qh5_vc1_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeRoomKickoutUsers&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"TotalPage": 1,
"TotalNum": 1,
"RequestId": "04CFEE1C-1D4D-4604-AB3C-3ACC3323D628"
"UserList": {
"User": [
{
"AppUid": "user-100",
"OpStartTime": "2018-05-24T08:58:26Z",
"OpEndTime": "2018-05-24T08:58:26Z"
}
]
}
}
```

## 特殊错误码 {#section_jc5_dd1_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

