# Configure HTTPS secure acceleration {#concept_e3y_jck_bfb .concept}

Hypertext Transfer Protocol over Secure Socket Layer \(HTTPS\) is a security suite of the normal HTTP channel focusing on security. It encapsulates HTTP with the SSL/TLS protocol with SSL/TLS protocol as its security base.

**Note:** **Terms in the console have been updated, and we will update the documentation as soon as possible. We are sorry for any inconvenience caused**.

## Advantages of HTTPS acceleration {#section_ffb_gvf_cfb .section}

Key user data is encrypted during transmission to prevent sensitive information from the leakage, such as session IDs or cookies that can be maliciously used by attackers.

Data integrity verification is performed during transmission to prevent the hidden danger of man in the middle \(MITM\) such as DNS or content hijacked or tampered by an unverified third party.

Alibaba Cloud ApsaraVideo Live provides HTTPS secure acceleration schemes. You must enable the secure acceleration mode and then upload the certificate/private key of the CDN domain name. The ApsaraVideo Live console also supports viewing, disabling, enabling, and editing the certificates.

If the certificate is configured correctly and enabled, both HTTP access and HTTPS access are supported. If the certificate does not match or is disabled, only HTTP access is supported.

## Attentions {#section_c55_hvf_cfb .section}

Configuration restrictions

|Feature|Description|
|:------|:----------|
|**Disable** and **Enable** HTTPS status|**Disable:** No HTTPS requests are supported and no certificate/private key information is retained. **Enable** You must re-upload the certificate/private key to enable the certificate again.|
|View certificate|It allows you to view the certificate only. Viewing private key information is not supported.|
|Modify and edit certificate|Modification and editing of the certificate are supported, but the effective period for performing these operations is 1 hour. Perform the operation with caution.|

Certificate restrictions

-   The certificate and private key of a CDN domain name for which **HTTPS Secure Acceleration** is enabled, must be uploaded. Both the certificate and private key must be in PEM format.

**Note:** Tengine used in ApsaraVideo Live is based on Nginx, which means certificates that can be read by Nginx are supported \(the certificates must be in PEM format\).

-   Only SSL/TLS handshakes containing SNI information is supported.

-   The certificate and private key that you upload must have a one-to-one correspondence with each other; otherwise, the verification fails.

-   The effective period of the updated certificate is 1 hour.

-   Private key with a password is not supported.


## Procedure {#section_kyl_kwf_cfb .section}

Step 1. Buy a certificate

To enable **HTTPS Secure Acceleration**, you must have a certificate that matches the CDN domain name. Click **Buy Now** at the ApsaraVideo Live Certificates Service to buy a certificate.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011633_en-US.png)

Step 2. Configure the ApsaraVideo Live domain name

1.  Enable HTTPS secure acceleration.
    1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
    2.  Click **Domain Names**, select the Streaming Domain Name that you want to configure HTTPS secure acceleration, and click **Configure**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011635_en-US.png)

    3.  Click **HTTPS Settings**, and click **Modify Configuration** following **HTTPS Certificate**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011636_en-US.png)

    4.  In **HTTPS Configuration**, enable **HTTPS Secure Acceleration** to go to the **Certificate Status**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011637_en-US.png)

2.  Select a certificate.

    Alibaba Cloud ApsaraVideo Live supports two types of certificates for deployment.

    -       -       -   Alibaba Cloud certificate: Certificates purchased from the ApsaraVideo Live Certificates Service are supported. You can select a certificate name to adapt to the CDN domain name.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011638_en-US.png)

**Note:** Only certificates in PEM format are supported.

3.  Set the redirect type.

    Click **Change Settings** following **Redirect Type**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849011639_en-US.png)

    Forcible Redirect is supported: The system forces redirect of the users’ original request methods by default.

    For example, if **HTTP \> HTTPS** redirect is enabled and a user initiates an HTTP request, the server returns a 302 redirect response and the original HTTP request is forcibly redirected to the HTTPS request.

    -   **Default**: HTTP and HTTPS requests are compatible.

    -   **HTTP \> HTTPS** redirect: Users’ HTTP requests are forcibly redirected to the HTTPS requests.

    -   **HTTPS \> HTTP** redirect: Users’ HTTPS requests are forcibly redirected to the HTTP requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849111640_en-US.png)


Step 3. Verify whether the certificate has taken effect

You can access resources by HTTPS when the configurations are completed and the certificate is enabled now. If a green HTTPS mark appears in your browser, it indicates that currently a private connection is established with the website and HTTPS secure acceleration is effective.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20692/154598849111641_en-US.png)

