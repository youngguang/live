# DescribeLiveSnapshotDetectPornConfig {#reference3291 .reference}

查询审核配置。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveSnapshotDetectPornConfig|系统规定参数。取值：DescribeLiveSnapshotDetectPornConfig|
|DomainName|String|是|www.yourdomain.com|用户域名。|
|AppName|String|否|testApp|app名，如不给出表示域名下所有的。|
|Order|String|否|asc|排序。

-   Asc：升序。
-   Desc：降序。

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
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|该条任务请求ID。|
|LiveSnapshotDetectPornConfigList| | |审核配置，只在正确返回时有。|
|  └DomainName|String|live.aliyunlive.com|用户域名。|
|  └AppName|String|xxx02|app名。|
|  └Interval|Integer|80|采样间隔。|
|  └OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OSSEndpoint的名称。|
|  └OssBucket|String|test123|OSS的Bucket名称。|
|  └OssObject|String|\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}\_\{Second\}.jpg|OSSObject的名称。|
|  └Scenes|String|porn| 检测场景，包括“porn”、“terrorism”、“ad”、“live”。

 默认值：“porn”

 |
|PageNum|Integer|1|分页的页码。|
|PageSize|Integer|2|每页大小。|
|Order|String|desc|排序。|
|TotalPage|Integer|11|总页数。|
|TotalNum|Integer|6|符合条件的总个数。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com/?Action=DescribeLiveSnapshotDetectPornConfig&DomainName=live.aliyunlive.com&AppName=xxx<公共请求参数> 
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "LiveSnapshotDetectPornConfigList":{
        "LiveSnapshotDetectPornConfig":[
            {
                "AppName":"xxx01",
                "DomainName":"live.aliyunlive.com",
                "Interval":80,
                "OssBucket":"bucket",
                "OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
                "OssObject":"{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg"
            },
            {
                "AppName":"xxx02",
                "DomainName":"live.aliyunlive.com",
                "Interval":80,
                "OssBucket":"bucket",
                "OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
                "OssObject":"{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg"
            }
        ]
    },
    "Order":"desc",
    "PageNum":1,
    "PageSize":2,
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "TotalNum":11,
    "TotalSize":6
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

## 错误码 {#section_ovf_3jh_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

