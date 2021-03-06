# EffectCasterUrgent {#concept_60265_zh .reference}

将指定场景画面紧急切换至备播视频，限制仅用于PGM场景的备播切换。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：EffectCasterUrgent|
|CasterId|String|是|导播台ID|
|SceneId|String|是|场景ID，PGM场景时有效|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=EffectCasterUrgent&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&SceneId=242b4e2c-c30f-4442-85ba-2e3e4e3dec1b&<公共请求参数> 
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
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|UrgentMaterialNotFound|Urgent material is not found|404|备播资源不存在|
|InvalidScene.NotFound|Scene is not found.|404|指定场景不存在|
|IncorrectSceneStatus|Scene is not started.|400|场景状态不允许当前操作|
|InvalidLayout.NotFound|Layout is not found.|400|指定场景不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

