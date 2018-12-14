# API authentication rules {#concept_67880_zh .concept}

## Introduction { .section}

Use RAM to give a subaccount access to its primary account’s live video resources.

-   You can activate the Live service through an Alibaba Cloud account and create a CDN domain name, then all the live functions and CDN domain names are held as resources of this account. By default, accounts have full operation permissions on their resources.

-   If you want to use Alibaba Cloud Resource Access Management \(RAM\) service, you can grant RAM sub-users the permission to access and manage the resources under your Alibaba Cloud account.

-   Read Set subaccounts to log on to the ApsaraVideo Live console by using RAM set carefully before learning how to use RAM to grant authorization and access to live service.

-   If you do not need to use RAM, skip this section.


## Authentication rules { .section}

When a subaccount uses live service APIs to access live resources of primary account, the live service background performs RAM access examination to make sure the resource owner grants the caller the relavant access to relevant resources.

Each differrent liver service API determines the permissions of which resources are to be examined according to the involved resources and the meaning of API. The authentication rules of each API are listed as follows.

|Action-name|Resource|
|:----------|:-------|
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

