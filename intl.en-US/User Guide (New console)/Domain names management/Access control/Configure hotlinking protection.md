# Configure hotlinking protection {#concept_84745_zh .concept}

The hotlinking protection function is realized based on the HTTP referrer mechanism where the referrer is used for source tracking and source identification. Users can configure a referrer blacklist or whitelist to identify and filter visitors in order to limit access to live video distribution resources.

Currently, the hotlinking protection function supports the blacklist or whitelist mechanism. After a visitor initiates a request for a resource, and the request arrives at a CDN node. The CDN node filters the identity of the visitor based on the preset hotlinking protection blacklist or whitelist. If the identity complies with the rules, the visitor can access the requested resource; and if the identity fails to comply with the rules, the request will be forbidden and a 403 response code is returned.

## Attentions { .section}

-   This function is optional and is disabled by default.

-   To enable this function, you can edit Blacklist or Whitelist. The Blacklist and Whitelist are mutually excluded, and you cannot configure both of them. This article takes the blacklist setting as an example.

-   You can set whether a null referrer field can be used to access CDN resources \(That is, whether to allow direct access to resource URL by using a browser’s address bar\).

**Note:** 

-   Generally, mobile ends cannot get referrers. Therefore, the system currently supports access with a null referrer field by default. If you have set the system, and it does not support access with a null referrer field, you can set the referrer in combination with Alibaba Cloud player at the mobile end. For more information, see [Basic player](https://www.alibabacloud.com/help/doc-detail/61431.htm?spm=a2c63.l28256.b99.202.126c7ad7lIUOpN).

-   If you forbid access with a null referrer field, make sure to configure **HTTPS secure acceleration**, and enable force redirection to HTTPS \(**HTTP \> HTTPS**\). When processing an HTTPS request for HTTP resources, some browsers remove the referred field and result in access failure.

-   After this function is enabled, wildcard domain names are automatically supported. For example, if you enter `a.com`, the final effective configuration is `*.a.com`. That is, all the sub-domains take effect.


## Procedure { .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domains**.
3.  Select the Streaming Domain to be configured, and click **Domain Settings**.
4.  Click **Access Control**.
5.  Select **Hotlinking Protection**, and click **Change Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154771564021668_en-US.png)

6.  Select the **Blacklist**, and add a specified domain name in **Referrers**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154771564021669_en-US.png)

     **Blacklist** is added successfully.

    **Note:** You can configure only one format of the hotlinking protection function, that is, only one of the blacklist and the whitelist can be configured at the same time.


