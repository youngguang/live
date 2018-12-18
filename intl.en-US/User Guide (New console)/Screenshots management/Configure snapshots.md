# Configure snapshots {#concept_84940_zh .concept}

ApsaraVideo Live snapshots service supports taking snapshots of the live video being played at a set interval and storing the snapshots as .jpg files to a specified location in OSS.

Under an ApsaraVideo Live acceleration domain name, the live snapshot settings are differentiated by the AppName of the live streaming. That is, all the streams under the same AppName perform snapshot operations following the settings of this AppName. The AppName can be set to ＊, indicating that all the streams under the acceleration domain name follow the snapshot settings.

To conveniently view the snapshots, set a bucket for storage first.

1.  Log on to the [ApsaraVideo Live console](https://home.console.aliyun.com/new#/).
2.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
3.  Click **Domain Names**.
4.  Select the Streaming Domain Name, and click **Manage Templates** at the right side.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20711/154512695121829_en-US.png)

5.  Click **Snapshots**, and click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20711/154512695121830_en-US.png)

6.  In **Snapshot Capture Template**, enter the snapshot parameters, and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20711/154512695121831_en-US.png)

    -   Enter the **AppName** that you want to enable snapshots function.
    -   Enter **Snapshot Capture Interval**. It can be between 5 and 3,600 seconds.
    -   Select **Storage Location**.
    -   Select **Storage Mode**, that is **Overwrite snapshot** or **Real-time snapshot**. You can also select both.

        -    **Overwrite**: The video snapshots are taken in sequence based on the set interval, and the new snapshot overwrites the previous one.
        -    **Create New**: The video snapshots are taken in sequence based on the set interval, and the new snapshots are stored in OSS in the order of N+1 \(N ≥ 0\).
        **Note:** The bucket and the current domain name must be in the same region. For example, if the current domain name is located in **China East 2 \(Shanghai\)**, the bucket must also be located in **China East 2 \(Shanghai\)**. If no bucket list is available in the panel, confirm whether the OSS bucket and the domain name are in the same region.

    In **Snapshots**, all the snapshots configurations are listed under the domain name. For example, all the live streams of which the **AppName** is **app** performs the snapshots operation based on this configuration.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20711/154512695121832_en-US.png)

    **Note:** After you modify the snapshots configuration, the new snapshots configuration takes effect for the next push streaming operation.


