# AllowPushStream {#reference_rxz_5y_lfb .reference}

解除禁止推流，用于被禁止推流后的房间恢复推流权限。

## 请求参数 {#section_zht_kny_lfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值： AllowPushStream|
|AppId|String|是|业务方APP ID。|
|RoomId|String|是|房间号，最多16位字符。|

## 返回参数 {#section_mz1_m4y_lfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id。|

## 示例 {#section_rht_ymy_lfb .section}

请求示例

```
https://live.aliyuncs.com?Action=CreateRoom&AppId=xxxx&RoomId=xxx<公共请求参数>
```

返回示例

```

{
"RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
}
```

## 特殊错误码 {#section_cff_n4y_lfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

