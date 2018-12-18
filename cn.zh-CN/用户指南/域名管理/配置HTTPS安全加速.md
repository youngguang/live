# 配置HTTPS安全加速 {#concept_e3y_jck_bfb .concept}

安全超文本传输协议（Hyper Text Transfer Protocol over Secure Socket Layer，简称 HTTPS），是以安全为目标的HTTP通道。简单来说，HTTPS 是 HTTP 的安全版，即将 HTTP 用 SSL/TLS 协议进行封装，HTTPS 的安全基础是 SSL/TLS。

## HTTPS 加速优势 {#section_ffb_gvf_cfb .section}

传输过程中对用户的关键信息进行加密，防止类似 Session ID 或者 Cookie 内容被攻击者捕获造成的敏感信息泄露等安全隐患。

传输过程中对数据进行完整性校验，防止 DNS 或内容遭第三方劫持、篡改等中间人攻击（MITM）隐患。

阿里云直播服务提供 HTTPS 安全加速方案，仅需开启安全加速模式后上传加速域名证书/私钥，并支持对证书进行查看、停用、启用、编辑操作。

证书配置正确且处于开启状态，同时支持 HTTP 访问和 HTTPS 访问。证书不匹配或者停用证书，仅支持 HTTP 访问。

## 注意事项 {#section_c55_hvf_cfb .section}

配置相关

|功能|说明|
|:-|:-|
|**停用** 和 **启用** HTTPS 功能|**停用** 后，不支持 HTTPS 请求且将不再保留证书/私钥信息。**启用** 后，再次开启证书，需要重新上传证书/私钥。|
|查看证书|允许用户查看证书，但是只支持查看证书，由于私钥信息敏感不支持私钥查看，请您妥善保管证书相关信息。|
|修改编辑证书|支持修改编辑证书，但注意生效时间是 1 小时，请慎重操作。|

证书相关

-   开启 **HTTPS 安全加速** 功能的加速域名，须上传证书，包含证书/私钥，均为 PEM 格式。

**说明：** 直播服务采用的 Tengine 服务是基于 Nginx 的，因此只支持 Nginx 能读取的证书，即 PEM 格式。

-   只支持带 SNI 信息的 SSL/TLS 握手。

-   您上传的证书和私钥要匹配，否则会校验出错。

-   更新证书的生效时间是 1 小时。

-   不支持带密码的私钥。


## 操作步骤 {#section_kyl_kwf_cfb .section}

步骤一、购买证书

开启 **HTTPS 安全加速**，需要具备匹配加速域名的证书。您可以在 [云盾证书服务](https://common-buy-intl.aliyun.com/?spm=5176.2020520163.cas.1.73638270UmF5c9&commodityCode=cas_intl&accounttraceid=5c6c3d4e-adf8-46ee-9dee-500a6cbc4e20#/buy) 单击 **立即购买**，购买证书。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606411633_zh-CN.png)

步骤二、配置直播域名

1.  打开 HTTPS 安全加速。
    1.  登录 [视频直播控制台](https://live.console.aliyun.com/?spm=a2c4g.11186623.2.5.41ef7726m6GZqV#/live/domains)。
    2.  单击 **域名管理**，选择需要配置HTTPS安全加速的播流域名，并单击 **域名配置**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606411635_zh-CN.png)

    3.  单击 **HTTPS配置**，并单击 **HTTPS证书**下方的 **修改配置**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606411636_zh-CN.png)

    4.  在 **HTTPS设置** 中，开启 **HTTPS安全加速** 按钮，进入开启 **证书状态**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606411637_zh-CN.png)

2.  选择证书。

    阿里云直播服务支持两种证书部署。

    -   自有证书：需要设置证书名称后上传证书内容和私钥，该证书将会在 [云盾证书控制台](https://yundun.console.aliyun.com/?spm=a2c4g.11186623.2.9.41ef7726m6GZqV&p=cas#/cas/home)保存，可以在 **我的证书** 部分查看。

    -   自有证书：需要设置证书名称后上传证书内容和私钥，该证书将会在 [云盾证书控制台](https://partners-intl.aliyun.com/login-required#/yundun) 保存，可以在 **我的证书** 部分查看。

    -   阿里云证书：支持在云盾证书服务购买过的证书，可以通过证书名称直接选择适配该加速域名。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606511638_zh-CN.png)

**说明：** 仅支持 PEM 的证书格式。

3.  设置跳转类型。

    单击 **跳转类型** 下方的 **修改配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606511639_zh-CN.png)

    支持设置强制跳转，即自定义将用户的原请求方式进行强制跳转。

    例如，开启 **HTTP \> HTTPS** 跳转后，用户发起了一个 HTTP 请求，服务端返回 302 重定向响应，原来的 HTTP 请求强制重定向为 HTTPS 请求。

    -   **默认**：兼容用户的 HTTP 和 HTTPS 请求。

    -   **HTTP \> HTTPS** 跳转：用户的请求将强制重定向为 HTTPS 请求。

    -   **HTTPS \> HTTP** 跳转：用户的请求将强制重定向为 HTTP 请求。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606511640_zh-CN.png)


步骤三、验证证书是否生效

设置完成待证书生效后，使用 HTTPS 方式访问资源，如果浏览器中出现绿色 HTTPS 标识，表明当前与网站建立的是私密连接，HTTPS 安全加速生效。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154512606511641_zh-CN.png)

