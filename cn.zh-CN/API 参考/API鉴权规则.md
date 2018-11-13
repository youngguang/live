# API鉴权规则 {#concept_67880_zh .concept}

## 简介 { .section}

借助 RAM 实现子账号对主账号的视频直播资源访问。

-   您可以通过云帐号开通 Live 服务，创建加速域名，所有直播的功能和加速域名都是该帐号拥有的资源。默认情况下，帐号对自己的资源拥有完整的操作权限。

-   如果您需要使用阿里云的访问控制 RAM（Resource Access Management）服务，您可以将您云账号下视频直播服务的访问及管理权限授予 RAM 中子用户。

-   在了解如何使用 RAM 来授权和访问直播服务之前，请仔细阅读RAM 产品文档。

-   如您不需要使用 RAM，请略过此章节。


## 鉴权规则 { .section}

当子账号通过直播服务 API 对主账号的直播资源进行访问时，直播服务后台向 RAM 进行权限检查，以确保资源拥有者的确将相关资源的相关权限授予了调用者。

每个不同的直播服务 API 会根据涉及到的资源以及 API 的语义来确定需要检查哪些资源的权限。每个 API 的鉴权规则具体见下表。

|Action-name|资源\( Resource \)|
|:----------|:---------------|
|DescribeLiveStreamsPublishList|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamsOnlineList|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamsBlockList|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamsControlHistory|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamOnlineUserNum|acs:cdn:\*:$accountid:domain/$domainName|
|ForbidLiveStream|acs:cdn:\*:$accountid:domain/$domainName|
|ResumeLiveStream|acs:cdn:\*:$accountid:domain/$domainName|
|SetLiveStreamsNotifyUrlConfig|acs:cdn:\*:$accountid:domain/$domainName|
|AddLiveAppRecordConfig|acs:cdn:\*:$accountid:domain/$domainName|
|CreateLiveStreamRecordIndexFiles|acs:cdn:\*:$accountid:domain/$domainName|
|DeleteLiveAppRecordConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveRecordConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamRecordContent|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamRecordIndexFile|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamRecordIndexFiles|acs:cdn:\*:$accountid:domain/$domainName|
|AddLiveStreamTranscode|acs:cdn:\*:$accountid:domain/$domainName|
|DeleteLiveStreamTranscode|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamTranscodeInfo|acs:cdn:\*:$accountid:domain/$domainName|
|AddLiveAppSnapshotConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DeleteLiveAppSnapshotConfig|acs:cdn:\*:$accountid:domain/$domainName|
|UpdateLiveAppSnapshotConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveSnapshotConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamSnapshotInfo|acs:cdn:\*:$accountid:domain/$domainName|
|AddLiveSnapshotDetectPornConfig|acs:cdn:\*:$accountid:domain/$domainName|
|AddLiveDetectNotifyConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveSnapshotDetectPornConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveDetectNotifyConfig.md|acs:cdn:\*:$accountid:domain/$domainName|
|UpdateLiveSnapshotDetectPornConfig|acs:cdn:\*:$accountid:domain/$domainName|
|UpdateLiveDetectNotifyConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DeleteLiveSnapshotDetectPornConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DeleteLiveDetectNotifyConfig|acs:cdn:\*:$accountid:domain/$domainName|
|DescribeLiveStreamsFrameRateAndBitRateData|acs:cdn:\*:$accountid:domain/$domainName|

