# DeleteCasterEpisode {#concept_hgm_5fd_pfb .concept}

删除导播台节目。

## 请求参数 {#section_wbs_wdd_pfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteCasterEpisode|
|CasterId|String|是|导播台Id|
|EpisodeId|String|是|节目Id|

## 返回参数 {#section_fz3_12d_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|requestId|String|该条任务请求Id|

## 示例 {#section_l4v_c2d_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DeleteCasterEpisode&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&EpisodeId=a2b8e671-2fe5-4642-a2ec-bf9327388752&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 特殊错误码 {#section_ktw_22d_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|InternalError|500|内部错误|

