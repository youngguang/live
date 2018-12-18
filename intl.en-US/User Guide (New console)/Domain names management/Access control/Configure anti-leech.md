# Configure anti-leech {#concept_84745_zh .concept}

The anti-leech function is realized based on the HTTP referrer mechanism where the referer is used for source tracking and source identification. Users can configure a referer blacklist or whitelist to identify and filter visitors in order to limit access to live video distribution resources.

Currently, the anti-leech function supports the blacklist or whitelist mechanism. After a visitor initiates a request for a resource, and the request arrives at a CDN node. The CDN node filters the identity of the visitor based on the preset anti-leech blacklist or whitelist. If the identity complies with the rules, the visitor can access the requested resource; and if the identity fails to comply with the rules, the request will be forbidden and a 403 response code is returned.

## Attentions { .section}

-   This function is optional and is disabled by default.

-   To enable this function, you can edit Blacklist or Whitelist. The Blacklist and Whitelist are mutually excluded, and you cannot configure both of them. This article takes the blacklist setting as an example.

-   You can set whether a null referer field can be used to access CDN resources \(That is, whether to allow direct access to resource URL by using a browser’s address bar\).

**Note:** 

-   Generally, mobile ends cannot get referers. Therefore, the system currently supports access with a null referer field by default.

-   If you forbid access with a null refered field, make sure to configure **HTTPS secure acceleration**, and enable force redirection to HTTPS \(**HTTP \> HTTPS**\). When processing an HTTPS request for HTTP resources, some browsers remove the refered field and result in access failure.

-   After this function is enabled, wildcard domain names are automatically supported. For example, if you enter `a.com`, the final effective configuration is `*.a.com`. That is, all the sub-domains take effect.


## Procedure { .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names**.
3.  Select the Streaming Domain Name to be configured, and click **Configure**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154512610121664_en-US.png)

4.  Click **Access Control**.
5.  Select **Referrer Spam Settings**, and click **Change Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154512610121668_en-US.png)

6.  Select the **Blacklist**, and add a specified domain name in **Rule**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154512610121669_en-US.png)

     **Blacklist** is added successfully.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20695/154512610121670_en-US.png)

    **Note:** You can configure only one format of the anti-leech function, that is, only one of the blacklist and the whitelist can be configured at the same time.


