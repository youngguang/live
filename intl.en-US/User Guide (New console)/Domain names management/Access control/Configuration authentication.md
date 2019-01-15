# Configuration authentication {#concept_85018_zh .concept}

URL authentication function aims to protect the user’s website content from the illegal or malicious behavior. Using anti-leech to add a referrer whitelist and blacklist can solve some hotlinking problems. However, the referrer anti-leech cannot protect the site resource because the referrer content can be falsified. Therefore, using URL authentication to protect the user’s source site resource is safer and more effective.

It is a safe and reliable anti-theft mechanism that protects site resources by coordinating Alibaba Cloud CDN acceleration node with customer’s resources site. The customer site provides customer with an encrypted URL \(including authentication information\), which the user then uses to make a request to the acceleration node. The acceleration node verifies the authentication information in the encrypted URL to determine the validity of the request \(that is, whether to respond normally to a valid response or refuse an invalid response\), thus effectively protecting customer site resources.

## Authentication URL composition { .section}

Authentication URL consists of Live streaming address/stream play address + verification string. The verification string is calculated according to md5 algorithm by using authentication key + expiration time. This address is applicable to PC end, mobile end, third-party push streaming and live streaming tools.

-    **Authentication KEY:** The field is assigned randomly, and also support custom configuration.

-    **Validity Period:** The time when user visits customer source server exceeds the self-defined time \(**timestamp** field designation\), the authentication is invalid. For example, if the validity period is 1800s, and the user sets the visit time as 2020-08-15 15:00:00, the link expires at 2020-08-15 15:30:00.


## URL authentication concept { .section}

Encrypted URL component

```
http://DomainName/Filename?auth_key=timestamp-rand-uid-md5hash

```

Authentication field description

|Field|Description|
|:----|:----------|
|timestamp|validity period, positive integer, fixed length 10, seconds measured from 1970-01-01. Used to control validity period, integer of 10 digit, expire time 1800s.|
|rand|random number, we recommend that you use UUID \(which cannot contain en dash”-“. For example, the format can be 477b3bbc253f467b8def6711128c7bec\).|
|uid|not used yet \(set to 0\)|
|md5hash|verification string calculated according to md5 algorithm, lowercase letters and numbers are supported, fixed length 32.|

When the server receives the request, it first determines whether the timestamp in the request is shorter than the current time. If it is shorter, then the validity period is thought to be invalid and it returns an HTTP 403 error. If the timestamp is longer than the current time, then a same string is structured \(see the following composition mode of sstring\). The server then calculates the HashValue according to MD5 algorithm, and compares this value with md5hash in the request. If the values are the same, then the authentication is successful; otherwise, it returns an HTTP 403 error.

HashValue is calculated with the following strings,

```
sstring = "URI-Timestamp-rand-uid-PrivateKey"（URI is the address corresponding to the user's request object, not including parameters，for example: /Filename）HashValue = md5sum(sstring)
HashValue = md5sum(sstring)

```

Examples

1.  Use **req\_auth** to request object. `http://cdn.example.com/video/standard/1K.html`
2.  Set the key to: aliyuncdnexp1234 \(set by the user\).
3.  The expire time of authentication is 2015-10-10 00:00:00, the seconds calculated is 1444435200.
4.  The server structures a signature string used to calculate Hashvalue. `/video/standard/1K.html-1444435200-0-0-aliyuncdnexp1234`
5.  The server calculates HashValue according to the signature string. `HashValue = md5sum("/video/standard/1K.html-1444435200-0-0-aliyuncdnexp1234") = 80cd3862d699b7118eed99103f2a3a4f`
6.  The URL, when making a request, is `http://cdn.example.com/video/standard/1K.html?auth_key=1444435200-0-0-80cd3862d699b7118eed99103f2a3a4f`

    The calculated HashValue is consistent with md5hash = 80cd3862d699b7118eed99103f2a3a4f in the user’s request, and the authentication succeeds.


## URL authentication code example {#section_uj1_lgg_cfb .section}

For more information, see [Authentication code example](https://www.alibabacloud.com/help/doc-detail/57388.htm?spm=a2c63.p38356.b99.50.652e6523uRedUw).

## Procedure { .section}

**Note:** Authentication function is enabled by default. We recommend that you keep it enabled by default, so as to reduce the risk of bootlegging. If you want to disable the authentication function, contact your business manager or open a ticket.

When the authentication function is enabled, you can select default authentication or custom authentication based on your needs.

Default authentication

In default authorization, the authorization key is assigned randomly, and the Validity Period is 30 minutes. The authentication expires if the time exceeds 1800s.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Stream Management** \> **URL Generator** \> **Edge Ingest**.

    **Note:** The edge ingest function preferentially pushes your video streams to the optimal CDN node to minimize such problems as video lagging and slow stream-pulling ratio. We recommend that you preferentially select **Edge Ingest**.

3.  Select the **Streaming Domain**, and the associated **Ingest Domain** to be authenticated, enter the corresponding **Application Name** and **Stream Name**, and click **Generate URLs**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753935921651_en-US.png)

    **Note:** You can configure the authentication for the Ingest Domain and the Streaming Domain as needed. We recommend that you perform authentication on both domains so as to reduce the risk of bootlegging.

    You can get the authenticated Ingest URLs and Streaming URLs.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753935921652_en-US.png)


Custom authentication

If you don’t adopt default configuration, you can also customize **Primary KEY**, **Secondary KEY**, **Validity Period**, **Application Name** and **Stream Name** to generate **signed URL** for stream ingest.

1.  Log on to the ApsaraVideo Live console.
2.  Click **Domains**, select the domain that you want to perform customize authentication, and click **Domain Settings**.
3.  Click **Access Control**, select **URL Authentication**, and click **Change settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753935921658_en-US.png)

    You can also go to **Stream Management** \> **URL Generator** \> **Edge Ingest**, click **Access Control** following **Streaming Domain** and the associated **Ingest Domain** to quickly go to the custom authentication page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753935921659_en-US.png)

4.  In **URL Authentication** page, customize the**Primary KEY**, **Secondary KEY**, and **Validity Period**, and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753936021660_en-US.png)

    **Note:** **Primary KEY** is a key for calculating encrypted string. If the **Primary KEY** is changed, all URLs using the **Primary KEY** instantly becomes invalid. The **Secondary KEY**bridges the process of modifying the **Primary KEY**, that is, when you change the Primary KEY, the ingest URL or streaming URL using the **Primary KEY** does not become invalid instantly, and the **Secondary KEY** plays a transition role.

5.  In **Stream Management** \> **URL Generator** \> **Edge Ingest**, select the **Streaming Domain**, the associated **Ingest Domain** to be authenticated, and enter the corresponding **Application Name** and **Stream Name**, and click **Generate URLs**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20694/154753936021661_en-US.png)

    You can get the signed Ingest URLs and Streaming URLs.


