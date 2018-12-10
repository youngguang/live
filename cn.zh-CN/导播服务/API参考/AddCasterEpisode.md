# AddCasterEpisode {#concept_mkq_ycd_pfb .concept}

添加导播台节目。

## 请求参数 {#section_wbs_wdd_pfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：AddCasterEpisode|
|CasterId|String|是|导播台Id。|
|EpisodeType|String|是|节点类型。-   Resource-视频源，
-   Component-组件。

|
|EpisodeName|String|否|节目名称。|
|ResourceId|String|否|视频源Id。-   若节点类型为Resource时，参数有效且必输，
-   若节点类型为Component时无效。

|
|ComponentIds|String\[\]|否|组件列表。按照元素顺序由下而上排列，组件将与视频源同步切换。

-   若类型为Component时，参数必输，
-   若类型为Resource时非必输，输入时表示组件与视频源绑定并同步切换。

|
|StartTime|String|是|起始时间。-   UTC 格式
-   例如：2016-06-29T19:00:00Z

|
|EndTime|String|是|结束时间。-   UTC 格式
-   例如：2016-06-29T19:00:02Z

|
|SwitchType|String|否|切换策略。 -   TimeFirst-时间优先
-   ContentFirst-内容优先

直播类视频源只允许采用时间优先，当节点类型为Resource时有效。

|

## 返回参数 {#section_fz3_12d_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|EpisodeId|String|节目ID|

## 示例 {#section_l4v_c2d_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=AddCasterEpisode&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&EpisodeType=Resource&EpisodeName=program_name_1&ResourceId=a2b8e671-2fe5-4642-a2ec-bf93880e1a41&StartTime=2016-06-29T19:00:00Z&EndTime=2016-06-29T19:02:00Z&switchType=TimeFirst&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "EpisodeId": "21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 特殊错误码 {#section_ktw_22d_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|InternalError|500|内部错误|

