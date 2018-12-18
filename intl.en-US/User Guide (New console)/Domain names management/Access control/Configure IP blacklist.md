# Configure IP blacklist {#concept_85015_zh .concept}

ApsaraVideo Live supports blacklist rules. If an IP is added to the blacklist, the IP cannot access the current CDN domain name.

## Attentions { .section}

IP blacklist currently supports adding IP network segment. For example, 127.0.0.1/24.

Wherein, 24 indicates that the first 24 bits of the subnet mask are effective. That is, 32-24=8bit indicates host ID, and the subnet can contain 28- 2 = 254 hosts. Therefore, the 127.0.0.1/24 indicates the IP network segment range is 127.0.0.1~127.0.0.255.

## Procedure { .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names**, select the domain name, and click **Configure**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154512612621674_en-US.png)

3.  Click **Access Control** \> **IP Address Blacklist**, and click **Change Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154512612621675_en-US.png)

4.  In **IP Address blacklist**, enter the blacklist IP address.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154512612621676_en-US.png)

     **IP Address blacklist** is configured successfully.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154512612621677_en-US.png)


