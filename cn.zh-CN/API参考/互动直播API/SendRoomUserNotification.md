# SendRoomUserNotification {#reference_i3j_gj1_mfb .reference}

房间内用户通知消息，主要用户发送礼物的通知，适合向房间内的个人发送通知。

## 请求参数 {#section_tqs_hj1_mfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|true|操作接口名，系统规定参数，取值：SendRoomUserNotification|
|AppId|String|true|控制台创建应用所获取的AppID。|
|RoomId|String|true|房间号，最多16位字符。|
|AppUid|String|false|发送指令用户 ID，最多16位字符。|
|ToAppUid|String|true|接收指令用户 ID，最多16位字符。|
|Data|String|true|指令数据。|
|Priority|Integer|false|消息优先级 1，2，3。默认值：2

|

Priority：

-   高优先级且必达，适用于系统通知。\(Topic+QOS\_1\)
-   非优先但是必达，适用于房间管控消息。\(Topic+QOS\_1\)
-   非优先非必达，适用于个人任务类活动。\(Topic+QOS\_2\)

## 返回参数 {#section_zgw_kj1_mfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|MessageId​|String|消息 ID|

## 示例 {#section_irs_hj1_mfb .section}

请求示例

```
https://live.aliyuncs.com?Action=SendRoomUserNotification&AppId=xxxx&RoomId=xxx&AppUid=xxx&ToAppUid=xxx&Data=xxx&Priority=xxx
```

返回示例

```

{
"RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
"MessageId": "fkglhshiogsos8y93793w"
}
```

## 特殊错误码 {#section_fj2_rj1_mfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

