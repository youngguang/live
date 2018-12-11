# DescribeLiveSnapshotConfig {#reference2722 .reference}

查询域名下的截图配置。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveSnapshotConfig|系统规定参数。取值：DescribeLiveSnapshotConfig|
|DomainName|String|是|www.yourdomain.com|您的加速域名。|
|AppName|String|否|testApp| 直播流所属应用名称。

 \*表示查询针对域名的配置，不传表示查询该域名下所有的配置

 |
|Order|String|否|asc|排序。

-   asc：升序。
-   desc：降序。

默认值：Asc|
|PageNum|Integer|否|1| 分页的页码。

 默认值：1

 |
|PageSize|Integer|否|10| 每页大小。

 取值范围：\[5，30\]

 默认值：10

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|A3136B58-5876-4168-83CA-B562781981A0|该条任务请求 ID。|
|LiveStreamSnapshotConfigList| | |截图配置。|
|  └DomainName|String|xxx|加速域名|
|  └AppName|String|xxx|直播流所属的应用名称。|
|  └TimeInterval|Integer|10|截图周期。|
|  └CreateTime|String|2016-05-20T01:33:38Z|创建时间。|
|  └OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OSSEndpoint域名。|
|  └OssBucket|String|test123|OSSBucket的名称。|
|  └OverwriteOssObject|String|test123|OSS 存储文件名。|
|  └SequenceOssObject|String|test123|OSS 存储文件名。|
|PageNum|Integer|2|分页的页码。|
|PageSize|Integer|11|每页大小。|
|Order|String|asc|排序。|
|TotalPage|Integer|10|总页数。|
|TotalNum|Integer|6|符合条件的总个数。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=DescribeLiveSnapshotConfig&DomainName=xxxxx&AppName=xxx&StreamName=xxx<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "LiveStreamSnapshotConfigList":{
        "LiveStreamSnapshotConfig":[{
            "AppName":"xxx",
            "CreateTime":"2016-05-20T01:33:38Z",
            "DomainName":"xxx",
            "OssBucket":"bucket",
            "OssEndpoint":"endpoint",
            "OverwriteOssObject":"object",
            "SequenceOssObject":"object",
            "TimeInterval":10
        }]
    },
    "Order":"asc",
    "PageNum":1,
    "PageSize":10,
    "RequestId":"A3136B58-5876-4168-83CA-B562781981A0",
    "TotalNum":100,
    "TotalPage":10
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 {#section_h54_bnc_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

