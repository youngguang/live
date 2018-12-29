# ForbidPushStream {#reference_bmf_3d1_mfb .reference}

禁止推流，主要用于后台管理主播是否能推流。

## 请求参数 {#section_iyb_kd1_mfb .section}

|参数|类型|是否必须|描述|
|Action|String|是|操作接口名，系统规定参数，取值：ForbidPushStream|
|AppId|String|是|业务方APP ID。|
|RoomId|String|是|房间号，最多16位字符。|
|UserData|String|是|业务方自定义数据。|
|EndTime|String|是|为空表示永久禁流时间。格式：yyyy-MM-dd'T'HH:mm:ss'Z'

|

## 返回参数 {#section_mbh_nd1_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|

## 示例 {#section_fkr_jd1_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=ForbidPushStream&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
}
```

## 特殊错误码 {#section_d4x_qd1_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

