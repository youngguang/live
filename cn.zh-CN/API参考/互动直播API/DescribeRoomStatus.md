# DescribeRoomStatus {#reference_ecb_nwz_lfb .reference}

获取房间状态，可获取直播间的推端流状态。

## 请求参数 {#section_kjv_pwz_lfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRoomStatus|
|AppId|String|是|业务方APP ID。|
|RoomId|String|是|房间号，最多16位字符。|

## 返回参数 {#section_lzw_twz_lfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id。|
|RoomStatus|int|状态。-   0：流关闭
-   1：流开启
-   2：流中断

|

## 示例 {#section_djw_4wz_lfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeRoomStatus&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"Status": 1,
"RequestId": "1B495781-7837-448A-8DC0-30C40D111A79"
}
```

## 特殊错误码 {#section_xrw_5wz_lfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

