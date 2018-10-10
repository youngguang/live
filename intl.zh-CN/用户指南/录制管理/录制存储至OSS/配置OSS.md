# 配置OSS {#concept_84932_zh .concept}

如果要将直播录制下来的文件存储在OSS产品中，您需要先开通OSS服务、创建OSS bucket，授予直播写入OSS的权限，才能在OSS列表进行查看、下载、播放等操作。

## 开通OSS服务 { .section}

您需要先将视频直播开通OSS服务，并授予MTS访问权限。详情参见 [开通视频直播服务]()。

-    **OSS存储访问权限**：主要用于存储录制的视频。

-    **授予MTS访问权限**：用于MTS服务默认角色的授权策略，包括OSS、MNS、以及KMS的部分权限。


## 创建OSS bucket { .section}

1.  登录 [OSS控制台](https://oss.console.aliyun.com/index?spm=5176.2020520107.1002.d10oss.3dfe962ekybGY)。

2.  单击 **新建Bucket**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531463442750/%E5%8D%95%E5%87%BB%E6%96%B0%E5%BB%BAoss%20bucket.png)

3.  输入Bucket信息。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531463578144/%E8%BE%93%E5%85%A5%20bucket%20%E4%BF%A1%E6%81%AF.png)

**说明：** Bucket **区域** 与直播域名所在区域必须一致。如，直播域名所在区域是 **华东2**，因此，Bucket也必须选择 **华东2**。Bucket创建完成后，您可以根据使用需求来创建Bucket的文件夹。

4.  在左侧Bucket列表中，单击您创建的Bucket名称，并单击 **文件管理** \> **新建目录**。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531464251819/%E5%8D%95%E5%87%BBbucket%E5%90%8D%E7%A7%B0%EF%BC%8C%E5%B9%B6%E5%8D%95%E5%87%BB%E6%96%87%E4%BB%B6%E7%AE%A1%E7%90%86.png)

**说明：** 当您的录制文件较多时，创建目录是为了对录制内容进行分类，方便对录制内容进行管理。

5.  在 **新建目录** 中，输入 **目录名**，并单击 **确定**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531464451689/%E8%BE%93%E5%85%A5bucket%E7%9B%AE%E5%BD%95%E5%90%8D.png)


## 配置直播写入OSS权限 { .section}

从OSS中读取视频信息，建议您将OSS bucket配置为可读权限。具体根据您对于权限的需求而定。

1.  登录 [OSS控制台](https://oss.console.aliyun.com/index?spm=5176.2020520107.1002.d10oss.3dfe962ekybGY)。

2.  在bucket列表中，选择新建的bucket，并单击 **基础设置**。

3.  单击 **读写权限** 项下的 **设置**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531808038642/%E6%96%B0%E5%BB%BAbucket%20%E5%86%99%E5%85%A5%E6%9D%83%E9%99%90%E9%85%8D%E7%BD%AE.png)

4.  选择 **公共读**，并单击 **保存**。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531808420881/%E9%80%89%E6%8B%A9%20%E5%85%AC%E5%85%B1%E8%AF%BB%EF%BC%8C%E5%B9%B6%E5%8D%95%E5%87%BB%E4%BF%9D%E5%AD%98.png)

**说明：** 如果您想要配置bucket读写权限，必须先完成账号的实名认证。

    配置后，您可以登录 [视频直播控制台](https://live.console.aliyun.com/?spm=5176.8466029.aliyun_sidebar.4.45351450ahvZQe#/overview)，在 **直播管理** \> **录制文件管理** 中预览录制的视频。


## 配置CDN域名 { .section}

如录制文件存储在OSS中，您可以配置一个CDN加速域名，查看录制视频时会进行CDN加速服务。CDN会将您OSS存储的视频分发到全国各地的节点。用户访问时只需访问最近的CDN节点读取文件，而无需访问OSS的源文件，也不会消耗OSS的外网流量。不仅可提升边缘用户的访问速度和体验，同时，CDN的外网流量费用相对OSS外网流量较低，仅为OSS外网流量的50%，可有效的节省整体应用的网络费用。

1.  在您所创建的bucket页面，单击 **域名管理** \> **绑定用户域名**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531465415992/%E5%8D%95%E5%87%BB%E5%9F%9F%E5%90%8D%E7%AE%A1%E7%90%86%EF%BC%8C%E9%85%8D%E7%BD%AEcdn%20%E5%8A%A0%E9%80%9F%E5%9F%9F%E5%90%8D.png)

2.  在 **绑定用户域名** 中，配置CDN加速域名，并单击 **提交**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84932/cn_zh/1531465398323/%E8%BE%93%E5%85%A5cdn%E4%BF%A1%E6%81%AF%EF%BC%8C%E5%B9%B6%E5%8D%95%E5%87%BB%E6%8F%90%E4%BA%A4.png)

    如果您仅对视频进行存储，可不用配置CDN加速域名。

    **说明：** CDN加速域名与直播服务域名不能是同一个，请您分别进行配置。


