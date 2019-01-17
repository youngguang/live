# 配置 IP 黑名单 {#concept_85015_zh .concept}

支持黑名单规则，添加了黑名单的 IP，表示此 IP 无法访问当前加速域名。

## 注意事项 { .section}

IP 黑名单当前支持 IP 网段添加，例如：127.0.0.1/24。

其中，24表示采用子网掩码中的前24位为有效位，即用32-24=8bit来表示主机号，该子网可以容纳28- 2 = 254 台主机。故127.0.0.1/24 表示 IP 网段范围是：127.0.0.1~127.0.0.255。

## 操作步骤 { .section}

1.  登录 [视频直播控制台](https://home.console.aliyun.com/new#/)。
2.  单击 **域名管理**，选择所需的域名，并单击 **域名配置**。
3.  单击 **访问控制** \> **IP 黑名单**，并单击 **修改配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154771567421675_zh-CN.png)

4.  在 **IP 黑名单** 中，输入黑名单 IP。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154771567421676_zh-CN.png)

     **IP 黑名单** 配置成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20696/154771567421677_zh-CN.png)


