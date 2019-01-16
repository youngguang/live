# DeleteRoom {#reference_wf5_1fz_lfb .reference}

删除房间，在直播结束或不再使用此直播间时删除直播间。

## 请求参数 {#section_tpz_dvz_lfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteRoom|
|AppId|String|是|控制台创建应用所获取的AppID。|
|RoomId|String|是|房间号，最多16位字符。|

## 返回参数 {#section_q1k_1wz_lfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|

## 示例 {#section_up1_cvz_lfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DeleteRoom&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
}
```

## 特殊错误码 {#section_amz_dwz_lfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

