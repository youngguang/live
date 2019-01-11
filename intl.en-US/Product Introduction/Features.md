# Features {#concept_ux5_wj3_bfb .concept}

## Main functions and features { .section}

|Category|Feature|Description|
|:-------|:------|:----------|
|Live video capture|Ingest protocol|Supports ingest RTMP.|
|Ingest mode|Supports Alibaba Cloud’s ingest SDKs and Demos for iOS, Android, and Web, in addition to common third-party ingets softwares such as XSplit, and FMLE.|
|Push streaming device|Supports common third-party codes or boxes based on ingest RTMP.|
|Live video watching|Streaming protocol|Supports streaming RTMP, FLV, and HLS.|
|Streaming mode|Supports Alibaba Cloud stream playing SDKs and Demos for iOS, Android, and Web, in addition to common third-party streaming softwares such as VLC.|
|Stream pulling mode|Supports flv, rtmp, and m3u8|
|Live video management|Management mode|Supports graphical management and API management using the console.|
|Console management|Domain management|Creates, modifies, or deletes a domain name; and enables or disables a live video service.|
|Template management|Creates, modifies, or deletes transcoding, and snapshot templates.|
|Console statistics|Collects and queries the real-time downstream bandwidth, downstream traffic, online viewers, requests \(in the operator/region dimension\), and quantity and status of live streams.|
|Live recording|Supports FLV, MP4 and M3U8 recording, and supports custom recording time duration.|
|Live video snapshot|Supports real-time snapshot overwriting and storage, in addition to the custom snapshot frequency.|
|Real-time transcoding|Supports the LD, SD, HD, and UHD bit rate formats, and the adaptive aspect ratio of transcoded videos.|
|Narrowband HD™ transcoding|Supports the LD, SD, HD, and UHD bit rate formats, and the adaptive aspect ratio of transcoded videos.|
|Live video security|URL authentication|Supports custom authentication key and expiration time.|
|IP blacklist|Restricts IP access to acceleration domain name.|
|Anti-referer list|Supports blacklist or white list.|
|Data statistics|Traffic statistics|Collects traffic data for statistics \(granularity of one day\).|
|Peak bandwidth statistics|Collects the peak bandwidth for statistics \(granularity of one day\).|
|Access statistics|Views UVs, access by location and other data.|
|Amount query|Queries transcoding, snapshot, recording and other data.|
|API management|Domain name management|Creates, deletes, modifies and queries domain name.|
|API traffic management| -   Creates, modifies, deletes, enables, or disables a live video domain.
-   Queries the number of current concurrent viewers.
-   Create, stop recording, etc.
-   Creates or stops a snapshot task.

 |
|Live recording|Uses ApsaraVideo Live console or API interfaces to record and store live videos to OSS.|
|Live video snapshots|Takes snapshots through the course of live broadcast and saves them to the Alibaba Cloud OSS platform using APIs.|
|Live video transcoding|Transcodes a live video to multiple formats using APIs.|
|SDK support|Ingest SDK|Real-time adjusting push streaming parameters, adaptive bit rate, frame rate, watermark and beautification parameters according to network condition of the streaming end.|
|Player SDK|Provides iOS, Android and Web player SDKs, support multiple playback format, and support one-second above-the-fold and time shifting.|
|Demo SDK|Quickly experience the whole process of push streaming and live streaming.|

## Edge ingest {#section_bkz_qvj_ggb .section}

**Introduction**

The edge ingest function preferentially pushes your video streams to the optimal CDN node to ensure that users can access the best uplink network. Besides, it can minimize such problems as video lagging and slow stream-pulling ratio caused by uplink transmission.

**Advantages**

Wide coverage: over 1,500 CDN nodes all over the world, and over 700 nodes in mainland China, covering mainstream cities and regions.

Intelligentization: to preferentially access the CDN node nearest users, so as to ensure the transmission stability.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21078/154719374435260_en-US.png)

## Premium Streaming\(Formerly global acceleration\) {#section_xdj_2kl_ggb .section}

**Introduction**

Premium streaming function aims to create a high-quality network transmission link between the video capture region and the play source station, so that the video can be transmitted using the shortest, and the optimal link between the video capture region and the play region, to help your business solve the problem of video lagging or high delay.

**Advantages**

Low-cost access: Access in a highly flexible way, and no development and server purchase costs are needed, the function is enabled when the configuration is completed.

High speed and stability: access and distribution from the nearest edge node, global nodes are connected by high-speed dedicated line.

Global coverage: mainstream regions such as Europe and America are covered.

Flexible sale: the service is billed with day as the time granularity, which supports the configuration of dedicated lines at stream level, to meet different user needs.

**Comparison between public network transmission with premium streaming**

|Functions|Public network|High-quality network transmission link|
|:--------|:-------------|:-------------------------------------|
|Communication quality and availability|The quality of long-distance public network communication is affected by a variety of factors, therefore, the delay stability and packet loss rate are difficult to guarantee.|Alibaba Cloud's high-quality infrastructure delivers enhanced link quality and availability.|
|Cost|On-demand payment of public network transmission fees|No hardware cost required. Flexible billing methods and affordable prices.|

