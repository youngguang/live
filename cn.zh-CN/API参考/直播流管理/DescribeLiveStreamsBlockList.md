# DescribeLiveStreamsBlockList {#concept_35410_zh .concept}

获取域名下直播流播放的黑名单。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamsBlockList|系统规定参数。取值：DescribeLiveStreamsBlockList|
|DomainName|String|是|www.yourdomain.com|您的加速域名。|
|PageNum|Integer|否|2| 取得第几页。

 默认值：1

 |
|PageSize|Integer|否|10| 每页大小，最大3000。取值范围：1~3000之前的任意整数。

 默认值：2000

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|DomainName|String|play.aliyunlive.com|流所属加速域名。|
|StreamUrls|String|play.aliyunlive.com/AppName/StreamName|流完整URL地址。|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|
|PageNum|Integer|2|分页的页码。|
|PageSize|Integer|10|每页显示的条数。|
|TotalNum|Integer|11|符合条件的总个数。|
|TotalPage|Integer|2|总页数。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com/?Action=DescribeLiveStreamsBlockList&DomainName=test101.aliyunlive.com&&PageSize=10&PageNum=2&<公共请求参数> 
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](https://help.aliyun.com/document_detail/50284.html) 。

正常返回示例

JSON格式

```
{
    "DomainName":"test101.cdnpe.com",
    "PageNum":2,
    "PageSize":10,
    "RequestId":"9D855EC8-CF71-4615-B164-F7DFCB23B41D",
    "StreamUrls":{
        "StreamUrl":["test101.cdnpe.com/app/stream1"]
    },
    "TotalNum":11,
    "TotalPage":2
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

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

