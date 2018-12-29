# SendRoomNotification {#reference_zqr_lh1_mfb .reference}

房间内通知消息，主要用于进出入房间的通知，适合在整个房间广播的消息通知。

## 请求参数 {#section_srt_mh1_mfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|true|操作接口名，系统规定参数，取值：SendRoomNotification|
|AppId|String|true|业务方APP ID。|
|RoomId|String|true|房间号，最多16位字符。|
|AppUid|String|false|发送用户 ID，最多16位字符。|
|Data|String|true|指令数据。|
|Priority|Integer|false|消息优先级：1，2，3。默认值：3

|

Priority：

-   高优先级且必达，适用于系统通知，付费礼物。\(Topic+QOS\_1\)
-   非优先但是必达，适用于房间管控消息，免费礼物。\(TopicLow+QOS\_1\)
-   非优先非必达，适用于出入房间通知类消息。\(TopicLow+QOS\_2\)

## 返回参数 {#section_uw2_nh1_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|MessageId|String|消息 ID|

## 示例 {#section_fst_mh1_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=SendRoomNotification&AppId=xxxx&RoomId=xxx&Data=xxx&Priority=xxx
```

返回示例

```

{
"RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"MessageId": "6445CA5D7FEE5B275DAB6AB2AC1B000C"
}
```

## 特殊错误码 {#section_ttq_x31_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

