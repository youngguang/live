# DescribeLiveUserDomains {#concept_88332_zh .concept}

查询用户名下所有的直播域名。 支持域名模糊匹配过滤、域名所处region过滤。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeUserDomains|操作接口名，系统规定参数，取值：DescribeLiveUserDomains|
|DomainName|String|否|\*.testdomain.com| 域名模糊匹配过滤。

 不传值，默认查询用户所有直播域名。

 |
|DomainSearchType|String|否|fuzzy\_match| 域名查询类型：

-   fuzzy\_match 模糊匹配，
-   pre\_match 前匹配，
-   suf\_match 后匹配，
-   full\_match 完全匹配，

 默认fuzzy\_match

 |
|DomainStatus|String|否|online| 域名状态过滤。域名状态包括：

-   online：运行中（表示域名服务状态正常），
-   offline：已停止，
-   configuring：配置中。

 |
|LiveDomainType|String|否|liveVideo| 直播域名业务类型。

 取值liveVideo或者liveEdge，不传查询所有。

 |
|PageNumber|Integer|否|1| 取得第几页。

 取值范围为：1~100000

 |
|PageSize|Integer|否|100| 分页大小。

-   默认值：20
-   最大值：50
-   取值：1~50之前的任意整数

 |
|RegionName|String|否|cn-beijing|域名所属region|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|E4EBD2BF-5EB0-4476-8829-9D94E1B15267|请求ID|
|PageNumber|Long|1|返回数据的页码|
|PageSize|Long|100|整页大小|
|TotalCount|Long|2|总条数|
|Domains| | |由 PageData 组成的数组格式，返回直播域名的状态信息|
|  └DomainName|String|live.yourdomain.com|直播域名名称|
|  └Cname|String|xingzu-bj.alivecdn.com.w.alikunlun.net|直播域名对应的CNAME域名|
|  └LiveDomainType|String|liveVideo|直播域名业务类型，取值liveVideo、liveEdge|
|  └GmtCreated|String|2017-08-29T12:15:36Z|直播域名创建时间|
|  └GmtModified|String|2017-12-29T12:15:36Z|直播域名修改时间|
|  └Description|String|test|备注|
|  └LiveDomainStatus|String|online| 直播域名状态。

 取值意义：

 - online表示启用，

 - offline表示停用，

 - configuring表示配置中，

 - configure\_failed表示配置失败，

 - checking表示正在审核，

 - check\_failed表c示审核失败。

 |
|  └RegionName|String|cn-beijing|域名所属的region|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 /?AccessKeyId=XxlctR6mMqO6mhXxX
&Action=DescribeLiveUserDomains
&DomainName=*.testdomain.com
&DomainSearchType=fuzzy_match
&DomainStatus=online
&LiveDomainType=liveVideo
&PageNumber=1
&PageSize=100
&RegionName=cn-beijing
&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "Domains":{
        "PageData":[
            {
                "Cname":"xingzu-bj.alivecdn.com.w.alikunlun.net",
                "Description":"",
                "DomainName":"xingzu-bj.alivecdn.com",
                "GmtCreated":"2017-08-29T12:15:36Z",
                "GmtModified":"2017-12-29T09:24:08Z",
                "LiveDomainStatus":"offline",
                "LiveDomainType":"liveVideo",
                "RegionName":"cn-beijing"
            },
            {
                "Cname":"kehan-bj.alivecdn.com.w.alikunlun.net",
                "Description":"浙ICP备12022327号",
                "DomainName":"kehan-bj.alivecdn.com",
                "GmtCreated":"2017-08-29T08:40:53Z",
                "GmtModified":"2017-12-29T09:24:12Z",
                "LiveDomainStatus":"offline",
                "LiveDomainType":"liveVideo",
                "RegionName":"cn-beijing"
            }
        ]
    },
    "PageNumber":1,
    "PageSize":100,
    "RequestId":"E4EBD2BF-5EB0-4476-8829-9D94E1B15267",
    "TotalCount":2
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4BE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

