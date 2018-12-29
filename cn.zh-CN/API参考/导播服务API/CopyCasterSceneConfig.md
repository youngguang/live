# CopyCasterSceneConfig {#reference1036 .reference}

将原场景配置应用至目标场景并生效，仅限PVW场景配置拷贝至PGM场景。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：CopyCasterSceneConfig|
|CasterId|String|是|导播台ID|
|FromSceneId|String|是|原场景ID，仅限于PVM场景|
|ToSceneId|String|是|目标场景ID，仅限于PGM场景|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=CopyCasterSceneConfig&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&FromSceneId=f1a361f4-bee3-436d-ae6e-d38e69437666&ToSceneId=05ab713c-676e-49c0-96ce-cc408da1b314&<公共请求参数> 
```

返回示例

JSON格式

```
{
    "RequestId": "CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 特殊错误码 {#section_yrr_gqh_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InvalidScene.NotFound|From scene is not found.|404|指定场景不存在|
|IncorrectSceneStatus|From scene is not started.|400|场景状态不允许当前操作|
|InvalidLayout.NotFound|Layout is not found.|400|指定场景不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

