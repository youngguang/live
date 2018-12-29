# CNAME解析 {#concept_ezj_2jb_yfb .concept}

添加域名后，您需要分别对推流域名和播流域名进行CNAME解析才可使用域名。

## 说明 {#section_fd5_jwj_bfb .section}

-   如果您的域名是在阿里云域名服务申请，请按照以下步骤操作。

-   如果您的域名不是在阿里云域名服务申请，可先将域名转入阿里云域名服务管理，执行 [域名转入流程](https://wanwang.aliyun.com/domain/transfers)，域名转入阿里云域名服务后，再按步骤执行 CNAME 绑定操作。

-   如果您的域名是通过其他途径申请，您也可以在域名所在网站进行CNAME绑定。

-   您需要分别对播流域名和推流域名进行CNAME解析操作。


## 操作步骤 {#section_ewq_kwj_bfb .section}

1.  登录 [视频直播控制台](https://live.console.aliyun.com/?spm=5176.2020520001.1001.56.Fcjldw#/live/domains)。
2.  单击 **域名管理**。
3.  选择所需的播流域名，并获取域名对应的CNAME。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65145/154453278533135_zh-CN.png)

    **说明：** CNAME 栏中有感叹号（！）提示的说明还没有配置CNAME信息。请您按照以下步骤配置CNAME信息。

4.  复制CNAME地址，进行域名解析。
    1.  登录 [域名控制台](https://netcn.console.aliyun.com/core/domain/list?spm=a2c4g.11186623.2.6.6d5a596dbOJz82)。
    2.  单击 **域名列表**。
    3.  选择需要配置解析的域名，并单击 **解析**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65145/154453278533136_zh-CN.png)

    4.  单击 **添加记录**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65145/154453278533137_zh-CN.png)

    5.  设置解析参数，并单击 **确定**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65145/154453278533138_zh-CN.png)

        -   在 **记录类型** 中，选择 **CNAME** 选项。
        -   在 **主机记录** 中输入播流地址二级域名。例如：播流域名是`a-play.aliyunlive.com`，则二级域名为`a-play`。
        -   在 **记录值**中，输入直播控制台域名列表中CNAME栏内容。
5.  播流域名进行CNAME解析之后，您需要按照同样的步骤对 **推流域名** 进行CNAME解析。

    **说明：** 解析参数设置后，CNAME 域名解析正常会很快生效。

    -   如果是新创建的域名，域名解析不存在 DNS 刷新问题。
    -   如果是修改了 CNAME，则不同的 DNS 上有缓存数据，可能最长需要48小时才能更新完毕。

