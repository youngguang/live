# Set subaccounts to log on to the ApsaraVideo Live console by using RAM {#concept_y3j_jgc_wfb .concept}

Through Alibaba Cloud Resource Access Management \(RAM\), you can provide required permissions to the subaccounts for the live broadcast in the ApsaraVideo Live console.

One primary account can create multiple subaccounts. By authorizing the subaccounts certain access functions, you can restrict their use of resources and functions for the purpose of unified management. For more information, see [What is RAM](../../../../../reseller.en-US/API Reference/Introduction/RAM introduction.md#).

Subaccount permissions mainly include authorization to use ApsaraVideo Live and OSS and CDN resource objects. We recommend that you plan the resource instances of such services for a subaccount, create authorization policies based on the corresponding authorization templates, and then grant the permissions to the subaccount.

## RAM restrictions {#section_akz_pgc_wfb .section}

RAM users cannot possess resources and they are not billed independently. These users are centrally controlled and billed under your Alibaba Cloud account. You can create separate passwords or keys for each RAM user, but these users do not have any operation permissions by default. RAM provides an access-policy-based authorization to help you grant fine-grained authority to the RAM users.

You must grant the following permissions to your subaccounts to use ApsaraVideo Live console functions:

Live \(Required\): Grants permission to use ApsaraVideo Live and uses the built-in **AliyunLiveFullAccess** authorization policy;

OSS \(Required\): Grants permission to use the screenshot storage service, which can be customized as needed; For more information, see the following content.

## Authorization operations {#section_q3m_ygc_wfb .section}

**Authorization on ApsaraVideo Live**

If a subaccount is required to use ApsaraVideo Live, you must grant the subaccount the permission to use ApsaraVideo Live. You can directly use the built-in `AliyunLiveFullAccess` authorization policy as follows:

1.  Log on to the [RAM console](https://partners-intl.aliyun.com/login-required#/ram).
2.  Click **Users**.
3.  Select User Name and click **Authorize** from the Actions column to grant the `AliyunLiveFullAccess`permission to the specified subaccount.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732528_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732529_en-US.png)


**MTS service authorization**

If a subaccount is required to use MTS, you must grant the subaccount the permission to use MTS. You can directly use the built-in`AliyunMTSFullAccess` authorization policy as follows.

1.  Log on to the RAM console.
2.  Click **Users**.
3.  Select User Name and click **Authorize** from the Actions column to grant the `AliyunMTSFullAccess`permission to the specified subaccount.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732533_en-US.png)


**Description of custom authorization policy creation**

You can customize authorization policies and assign them to specified subaccounts.

1.  Log on to the RAM console.
2.  Click**Policies**.
3.  Click **Custom Policy**.
4.  Click **Create Authorization Policy**to create custom authorization policies as the following samples for the specified resource instance and grant the policies to the specified subaccount.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732536_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732537_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732538_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732539_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732540_en-US.png)

    **Note:** After the authorization policies are created for various service resource objects, you can grant the permissions to the corresponding subaccounts.


The following are OSS and CDN authorization policies. You can grant corresponding permissions to subaccounts as needed.

**OSS authorization policy**

Permission description:

-   All operation permissions on specified buckets;
-   Permission to view the bucket list;

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "oss:*"
          ],
          "Resource": [
            "acs:oss:*:*:$Bucket",
            "acs:oss:*:*:$Bucket/*"
          ],
          "Effect": "Allow"
        },
        {
          "Action": [
            "oss:ListBuckets"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }
      ]
    }
    ```


**Live authorization policy**

Permission description:

-   All operation permissions on specified Live CDN domain name;
-   Permission to view the Live CDN domain name;

```
{
  "Version": "1",
  "Statement": [
    {
      "Action": "live:*",
      "Resource": [
        "acs:cdn:*:$Uid:domain/$DomainName"
      ],
      "Effect": "Allow"
    },
    {
      "Action": "live:Describe*",
      "Resource": "*",
      "Effect": "Allow"
    }
  ]
}
```

**Note:** The following variables are used in the resource authorization policies of each service. Replace them with your actual resource instance name:

## Description of variables {#section_dlq_qlc_wfb .section}

-   Uid

    **$Uid**: Alibaba Cloud account ID. You can query it through **Alibaba Cloud console** \> **Account Management** \> **Security Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154899299732544_en-US.png)

-   Bucket

    **$Bucket**: OSS bucket.

-   Live

    **$DomainName**: Live CDN domain name.


