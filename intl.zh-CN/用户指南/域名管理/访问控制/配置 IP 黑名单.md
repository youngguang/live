# 配置 IP 黑名单 {#concept_85015_zh .concept}

支持黑名单规则，添加了黑名单的 IP，表示此 IP 无法访问当前加速域名。

## 注意事项 { .section}

IP 黑名单当前支持 IP 网段添加，例如：127.0.0.1/24。

其中，24表示采用子网掩码中的前24位为有效位，即用32-24=8bit来表示主机号，该子网可以容纳28- 2 = 254 台主机。故127.0.0.1/24 表示 IP 网段范围是：127.0.0.1~127.0.0.255。

## 操作步骤 { .section}

1.  登录 [视频直播控制台](https://home.console.aliyun.com/new#/)。

2.  单击 **域名管理**，选择所需的域名，并单击 **域名配置**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/85015/cn_zh/1532767751192/%E5%8D%95%E5%87%BB%20%E5%9F%9F%E5%90%8D%E7%AE%A1%E7%90%86-%E5%9F%9F%E5%90%8D%E9%85%8D%E7%BD%AE.png)

3.  单击 **访问控制** \> **IP 黑名单**，并单击 **修改配置**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/85015/cn_zh/1531382947844/%E8%AE%BE%E7%BD%AE%20ip%E9%BB%91%E5%90%8D%E5%8D%95.png)

4.  在 **IP 黑名单** 中，输入黑名单 IP。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/85015/cn_zh/1533192803948/%E8%AE%BE%E7%BD%AEip%E9%BB%91%E5%90%8D%E5%8D%95%202.png)

     **IP 黑名单** 配置成功。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/85015/cn_zh/1533192828297/%E8%AE%BE%E7%BD%AEip%E9%BB%91%E5%90%8D%E5%8D%95%E6%88%90%E5%8A%9F.png)


