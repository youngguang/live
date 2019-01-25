# Store live recordings to OSS {#concept_84931_zh .concept}

ApsaraVideo Live allows you to record source video streams. It supports m3u8 \(.ts fragment files\), mp4, and flv format, along with recording duration configurations. Video files are stored in the bucket you specify in OSS. After a streaming ends, a recording index file for the streaming is generated automatically \(m3u8, mp4, or flv files\). The service also supports the generation of custom recording index files based on your specified recording start time and end time.

Under a live video CDN domain name, the live recording configurations are differentiated by the **AppName** and **StreamName**. That is, streams under the same**AppName** and **StreamName** all perform recording operations following the configurations for this **AppName** and **StreamName**.

## Introduction { .section}

-   To store live recordings to OSS, you must first enable OSS service, and provides ApsaraVideo Live service with the access authorization of writing in OSS. Then you can store videos in specific OSS bucket. For more information, see [Configure OSS](reseller.en-US/User Guide (New console)/Recording management/Store live recordings to OSS/Configure OSS.md#).

-   To avoid recorded files abnormally cut off due to network jitter or temporary stream disconnection during live recording, the system disconnects the stream until 180s. That is, if you perform another streaming operation within 180s after stream disconnection, the system judges it as the same stream by default; if the time interval exceeds 180s, the system judges it as two different streams.


## Create live recordings { .section}

1.  Log on to the[ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names.**.
3.  Select the stream play domain name, and click **Template Set**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154838653221779_en-US.png)

4.  In the left-side navigation pane, click **Recording**.
5.  Select **Store to OSS**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154838653221780_en-US.png)

    **Note:** To store live recordings to OSS, you must provide ApsaraVideo Live service with the access authorization of writing in OSS. Then you can store videos in specific OSS bucket. For more information, see [Configure OSS](reseller.en-US/User Guide (New console)/Recording management/Store live recordings to OSS/Configure OSS.md#).

6.  Add callback URL. For more information, see [Recording callback URL](reseller.en-US/User Guide (New console)/Recording management/Store live recordings to OSS/Recording callback URL.md#).
7.  Click **Add**, and enter recording parameters in **Recording Template**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154838653221781_en-US.png)

    -    **AppName**: The name of the video app. The **AppName** must be the same with the **AppName** of the live stream, or the configuration does not take effect. For example, the **AppName** in streaming address is `app`, and the **AppName** of the recording parameter must also be`app`. If you want to configure domain-level recording parameter, enter wildcard \(\*\).
    -    **StreamName**: The system supports recording at stream level. You can enter the stream name that you want to record. If you want to record all the streams under the `AppName`, enter wildcard \(\*\).

        **Note:** **AppName** and **StreamName** parameters support upper case letters, lower case letters, number, hyphen \(-\) and underline \(\_\). The length is limited within 255 characters.

    -    **Storage Format/Format**: The system supports **flv**, **m3u8**, and **mp4** formats.
    -    **Naming Conventions**：The default storage path for recordings is:

         `m3u8:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

         `ts:record/{AppName}/{StreamName}/{UnixTimestamp}_{Sequence}` 

         `mp4:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

         `flv:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

        In the example screenshot, the **AppName** is **app**, the **StreamName** is **stream**, so the **m3u8** and **ts** recording files are stored in the following path:

         `m3u8:record/app/stream/{EscapedStartTime}_{EscapedEndTime }` 

         `ts:record/app/stream/{UnixTimestamp}_{Sequence}` 

        If the default recording file storage path does not meet your requirements, you can modify it by using the API interface.

        To maintain compatibility with the streaming process, the recording system judge a live stream to have ended when an interruption caused by network jitter or another problem persists for **180 seconds** and the stream is not restored. The system independently stores the default recording index files \(m3u8 files\) in the format: `{AppName}/{StreamName}/{Date}.m3u8`.

    -    **Recording Cycle/Cycle**: The system supports **Recording Cycle/Cycle** from 15 to 360 minutes, that is 6 hours recording at most. If a recording time duration exceeds 6 hours, the system generates a new recording file according to the recording naming rule. The default time duration of **ts** fragments is 30 seconds.
    -   **Storage Path/Path**: The storage location of the recording.

        **Note:** The buckets list contains standard buckets and MPS buckets. The standard buckets are OSS buckets, used for storing; the MPS buckets are customized by MPS, and video stored in MPS bucket can perform MPS transcoding tasks. Currently, standard buckets and MPS buckets are not labelled in the buckets list. If you want to convert videos to media files, we recommend that you differentiate the name of the MPS bucket by yourself.

8.  Click **OK** to complete recording configuration.

    All the live streams of which the**AppName** is `app`, and the **StreamName** is `stream` under the domain name all perform recording operation according to this configuration. If you want to view recorded files, see [View recorded files](reseller.en-US/User Guide (New console)/Recording management/Store live recordings to OSS/View recorded files.md#).

    **Note:** The new recording configuration takes effect when you re-perform streaming operation. If you have started the streaming operation before the configuration, you must suspend the current streaming for more than 180s, and then re-configure streaming parameters.


