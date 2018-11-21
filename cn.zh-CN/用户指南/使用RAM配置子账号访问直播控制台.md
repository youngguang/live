# 使用RAM配置子账号访问直播控制台 {#concept_y3j_jgc_wfb .concept}

通过阿里云访问控制服务（RAM）可为子帐号授予相关权限，以达到子帐号在授权范围使用视频直播 \(ApsaraVideo Live\) 控制台的目的。

一个主账号可以创建多个子账号，通过对子账号功能的授权，可以限制子账号对主账号资源、功能的访问，达到统一管理的目的。了解[阿里云 RAM 服务](../../../../cn.zh-CN/API参考/API 参考（RAM）/简介/RAM简介.md#)。

子帐号的权限主要为直播服务使用授权及 OSS资源对象的权限，规划好该子帐号拥有这些服务的资源实例后即可按相应的授权模版创建授权策略，并授予给该子帐号即可。

## RAM的限制 {#section_akz_pgc_wfb .section}

RAM用户不允许拥有资源，没有独立的计量计费，这些用户由您的云账户统一控制和付费。您可以给每个RAM用户创建单独的登录密码或访问密钥。但在默认条件下，这些用户并没有任何操作权限。RAM提供基于访问策略的授权机制，支持您实现对 RAM 用户的细粒度授权。

使用直播控制台，必须给您的子账号开通以下授权才能正常使用服务。

Live （必选）授权使用直播服务，直接使用系统内置 **AliyunLiveFullAccess** 授权策略。

OSS （必选）授权使用截图存储服务，可按需自定义。详情参见下文。

## 授权操作 {#section_q3m_ygc_wfb .section}

**视频直播服务授权ApsaraVideo Live**

子账号若需要使用直播服务，需要授予子帐号视频直播服务使用权限。您可以直接使用系统内置`AliyunLiveFullAccess`授权策略。

1.  登录 [访问控制台](https://ram.console.aliyun.com/#/user/list)。
2.  单击 **用户管理**。
3.  选择用户名，并单击 **授权** 为指定的子帐号授予`AliyunLiveFullAccess`权限即可。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032528_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032529_zh-CN.png)


**媒体转码服务授权MTS**

子账号若要使用录制视频转码服务，需要授予子帐号媒体转码服务使用权限。您可以直接使用系统内置`AliyunMTSFullAccess`授权策略。

1.  登录访问控制台。
2.  单击 **用户管理**。
3.  选择用户名，并单击 **授权** 为指定的子帐号授予`AliyunMTSFullAccess`权限即可。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032533_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032535_zh-CN.png)


**自定义授权策略创建说明**

您可以自定义创建授权策略并指定给子账号。

1.  登录访问控制台。
2.  单击 **策略管理**。
3.  单击 **自定义授权策略**。
4.  单击 **新建授权策略** 为指定资源实例创建如下例举的自定义授权策略并授予指定的子帐号即可。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032536_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032537_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032538_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032539_zh-CN.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032540_zh-CN.png)

    **说明：** 各服务资源对象授权策略创建完毕后，为相应子帐号授予权限即可。


以下为 OSS 与 Live 授权策略，您可根据需求授予子账号相应权限。

**OSS授权策略**

权限描述：

-   对指定的Bucket有所有操作权限；
-   有查看Bucket列表权限。

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


**Live 授权策略**

权限描述：

-   对指定的Live加速域名有所有权限；
-   有查询Live加速域名的权限。

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

**说明：** 各个服务的资源授权策略中使用了如下变量，请您替换为您实际的资源实例名称。

## 变量说明 {#section_dlq_qlc_wfb .section}

-   Uid

    **$Uid**：云账号 ID，可通过 **控制台** \> **账号管理** \> **安全设置** 进行查询。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64551/154278047032544_zh-CN.png)

-   Bucket

    **$Bucket**：OSS bucket。

-   Live

    **$DomainName**：Live 加速域名名称。


