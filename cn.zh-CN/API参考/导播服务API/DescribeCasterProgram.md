# DescribeCasterProgram {#concept_ajf_4jd_pfb .concept}

查询导播台节目单。

## 请求参数 {#section_wbs_wdd_pfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterProgram|
|CasterId|String|是|导播台Id|
|EpisodeId|String|否|节目Id|
|EpisodeType|String|否|节点类型。-   Resource-视频源，
-   Component-组件。

|
|StartTime|String|否|查询范围。返回指定开始时间后开启的节目。

|
|EndTime|String|否|查询范围。返回指定结束时间前开启的节目。

|
|Page|Integer|否|页码|
|Rows|Integer|否|每页条数|
|Status|Integer|否|节目状态。-   0：未播放，
-   1：播放中，
-   2：播放完毕

|

## 返回参数 {#section_fz3_12d_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|CasterId|String|导播台Id|
|ProgramName|String|节目单名称|
|Episodes|\[\]Episode|节点列表|
|ProgramEffect|Integer|启用标志。-   0：不启用
-   1：启用

|

**Episode**

|参数|类型|描述|
|:-|:-|:-|
|EpisodeId|String|节目名称|
|EpisodeType|String|节点类型。-   Resource-视频源，
-   Component-组件。

|
|EpisodeName|String|节目名称|
|ResourceId|String|视频源Id|
|ComponentIds|String\[\]|组件列表|
|StartTime|String|起始时间。-   UTC 格式
-   例如：2016-06-29T19:00:00Z

|
|EndTime|String|结束时间。-   UTC 格式
-   例如：2016-06-29T19:00:00Z

|
|SwitchType|String|切换策略。-   TimeFirst-时间优先
-   ContentFirst-内容优先

直播节目只允许采用时间优先。|

## 示例 {#section_l4v_c2d_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeCasterProgram&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "ProgramId":"1872639A-F203-4EC5-8E43-CB92E68F8378",
    "ProgramName": "programs_name",
    "Episodes": [
        {
           "EpisodeId":"1872639A-F203-4EC5-8E43-CB92E68F8732",
           "EpisodeType":"Resource",
           "EpisodeName": "program_name_1",
           "ResourceId":"1872639A-F203-4EC5-8E43-CB92E8374827",
           "ComponentIds":[
                 "1872639A-F203-4EC5-8E43-CB9292827362"
            ],
           "StartTime": "2016-06-29T19:00:00Z",
           "EndTime": "2016-06-29T19:02:00Z",
           "Duration": 120.0,
           "SwitchType": "TimeFirst"
        },
        {
          "EpisodeId":"1872639A-F203-4EC5-8E43-CB92E6873726",
          "EpisodeType":"Component",
          "ComponentIds":[
            "1872639A-F203-4EC5-8E43-CB6253647382"
          ],
          "StartTime": "2016-06-29T19:02:00Z",
          "EndTime": "2016-06-29T19:04:00Z",
        }
    ]
}
```

## 特殊错误码 {#section_ktw_22d_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|InternalError|500|内部错误|

