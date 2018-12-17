# Configure CNAME {#concept_kkt_r5j_bfb .concept}

## Procedure {#section_ewq_kwj_bfb .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names**.
3.  Select the Streaming Domain Name, and copy the corresponding CNAME.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20690/154501262411550_en-US.png)

    **Note:** An exclamation mark \(!\) in CNAME indicates that the domain name has not complete CNAME configuration. For more information about configuring CNAME, see the following steps.

4.  Copy CNAME, and perform the CNAME configuration operation.
    1.  Log on to the [Domains console.](https://partners-intl.aliyun.com/login-required#/domain).
    2.  Click **Domain Names**.
    3.  Select the domain name you want to configure CNAME, and click **Resolve**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20690/154501262411551_en-US.png)

    4.  Click **Add Record**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20690/154501262411552_en-US.png)

    5.  Configure parameters, and click**OK**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20690/154501262411553_en-US.png)

        -   In **Type**, select **CNAME-Canonical name**.
        -   In **Host**, enter the secondary domain name of the Streaming URL. For example: the Streaming Domain Name is `a-play.aliyunlive.com`, then the secondary domain name is`a-play`.
        -   In **Value**, enter the CNAME you have copied from the domain name list.
5.  After you complete configuring CNAME for the Streaming Domain Name, you must perform the same operations for **Ingest Domain Name**.

    **Note:** After you configure the resolution parameters, the CNAME configuration normally takes effect quickly.

    -   If it is a newly created domain name, the resolution are not required to refresh the DNS.
    -   Different data is cached on different DNSs. And, if the CNAME changes, it may take up to 48 hours to complete the updates.

