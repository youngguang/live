# DeleteCasterVideoResource {#reference734 .reference}

删除视频资源。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteCasterVideoResource|
|CasterId|String|是|导播台ID|
|ResourceId|String|是|资源ID|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DeleteCasterVideoResource&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&ResourceId=05ab713c-676e-49c0-96ce-cc408da1b314&<公共请求参数>
```

返回示例

JSON格式

```
{
    "RequestId": "CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidResource.NotFound|Resource is not found.|404|指定资源不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

