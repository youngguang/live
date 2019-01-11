# Configure OSS {#concept_84932_zh .concept}

If you want to store live recorded files in the OSS product, you need to create the OSS bucket first, and grant the right to write to the OSS live, in order to view, download, play, and so on in the OSS list.

## Create an OSS bucket { .section}

1.  Log on to the [OSS console](https://partners-intl.aliyun.com/login-required#/OSS).
2.  Click **+** following Bucket.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621762_en-US.png)

3.  Enter Bucket information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621763_en-US.png)

    **Note:** After the bucket is created, check that the **region** of the bucket is consistent with that of the live video domain name. For example, the region of the live video domain name is **China East 2 \(Shanghai\)**, you must also select **China East 2 \(Shanghai\)** as the region of the bucket. You can also create bucket folders as needed.

4.  In the left-side buckets list, click the bucket you created, and click **Files** \> **Create Directory**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621764_en-US.png)

    **Note:** If you have many recording files, you can create folders to classify them so as to facilitate recording management.

5.  In **Create Directory**, enter **Directory Name**, and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621765_en-US.png)


## Configure OSS Access Control List \(ACL\) { .section}

If you want to read video information from OSS, we recommend that you configure the OSS bucket ACL as Public Read. The specific access authorization depends on your needs.

1.  Log on to the OSS console.
2.  In buckets list, select the bucket you created, and click **Basic Settings**.
3.  Click **Settings** following **Bucket ACL**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621766_en-US.png)

4.  Select **Public Read**, and click**Save**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621767_en-US.png)

    **Note:** You must first complete real-name registration, if you want to configure the bucket ACL.

    After completing configuration, you can log on to the ApsaraVideo Live console \> **Live Videos** \> **Recordings** to preview live recordings.


## Configure CDN domain name { .section}

If the live recordings are stored to OSS, you can configure a CDN domain name to perform CDN acceleration when you view live recordings. CDN delivers videos stored to OSS to nodes in China. Users access the nearest CDN node to read files without accessing the source files in OSS, which does not consume OSS Internet traffic. By using CDN, the access rate and experience of edge users are improved, and the CDN Internet traffic cost is only 50% of the OSS Internet traffic cost. This efficiently reduces the network fees for your applications.

1.  In the page of the bucket you created, click **Domain Names** \> **Bind User Domain**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621768_en-US.png)

2.  In **Bind User Domain**, configure CDN domain name, and click **Submit**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20702/154719950621769_en-US.png)

    If you just store your live recordings, you are not required to configure a CDN domain name.

    **Note:** CDN domain name and the live video domain name must be different. We recommend that you configure the CDN domain name and the live video domain name respectively.


