# 直播API概述 {#concept_mmr_bhl_bfb .concept}

请确保在使用这些接口前，已充分了解视频直播产品说明和收费方式。

当前Live Open API版本号为：2016-11-01。

## 术语表 {#section_n5h_bz5_cfb .section}

## 业务限制资源规格限制说明 {#section_arw_bz5_cfb .section}

见[附录](../../../../intl.zh-CN/旧版API参考/附录.md#)

## 直播截图 {#section_m3m_2z5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveAppSnapshotConfig](intl.zh-CN/API参考/直播截图/添加截图配置.md#)|添加截图配置|
|[DeleteLiveAppSnapshotConfig](intl.zh-CN/API参考/直播截图/删除截图配置.md#)|删除截图配置|
|[DescribeLiveSnapshotConfig](intl.zh-CN/API参考/直播截图/查询域名下的截图配置.md#)|查询域名下的截图配置|
|[DescribeLiveStreamSnapshotInfo](intl.zh-CN/API参考/直播截图/查询截图信息.md#)|查询截图信息|
|[UpdateLiveAppSnapshotConfig](intl.zh-CN/API参考/直播截图/更新截图配置.md#)|更新截图配置|

## 直播拉流 {#section_c5n_gz5_cfb .section}

|API|描述|
|:--|:-|
|[DeleteLivePullStreamInfoConfig](intl.zh-CN/API参考/直播拉流/删除拉流.md#)|删除拉流|
|[AddLivePullStreamInfoConfig](intl.zh-CN/API参考/直播拉流/添加拉流.md#)|添加拉流|
|[DescribeLivePullStreamConfig](intl.zh-CN/API参考/直播拉流/查询拉流信息.md#)|查询拉流信息|

## 状态通知 {#section_o1p_gz5_cfb .section}

|API|描述|
|:--|:-|
|[SetLiveStreamsNotifyUrlConfig](intl.zh-CN/API参考/状态通知/设置NotifyURL.md#)|设置NotifyURL|
|[DescribeLiveStreamsNotifyUrlConfig](intl.zh-CN/API参考/状态通知/查询NotifyURL.md#)|查询NotifyURL|
|[DeleteLiveStreamsNotifyUrlConfig](intl.zh-CN/API参考/状态通知/删除NotifyURL.md#)|删除NotifyURL|

## 直播录制 {#section_nfq_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveAppRecordConfig](intl.zh-CN/API参考/直播录制/添加APP录制配置.md#)|添加APP录制配置|
|[DeleteLiveAppRecordConfig](intl.zh-CN/API参考/直播录制/删除APP录制配置.md#)|删除APP录制配置|
|[DescribeLiveRecordConfig](intl.zh-CN/API参考/直播录制/查询域名下录制配置列表.md#)|查询域名下录制配置列表|
|[DescribeLiveStreamRecordContent](intl.zh-CN/API参考/直播录制/查询录制内容.md#)|查询录制内容|
|[CreateLiveStreamRecordIndexFiles](intl.zh-CN/API参考/直播录制/创建录制索引文件.md#)|创建录制索引文件|
|[DescribeLiveStreamRecordIndexFile](intl.zh-CN/API参考/直播录制/查询单个录制索引文件.md#)|查询单个录制索引文件|
|[DescribeLiveStreamRecordIndexFiles](intl.zh-CN/API参考/直播录制/查询录制索引文件.md#)|查询录制索引文件|
|[AddLiveRecordNotifyConfig](intl.zh-CN/API参考/直播录制/添加录制回调配置.md#)|添加录制回调配置|
|[DeleteLiveRecordNotifyConfig](intl.zh-CN/API参考/直播录制/删除录制回调配置.md#)|删除录制回调配置|
|[DescribeLiveRecordNotifyConfig](intl.zh-CN/API参考/直播录制/查询录制回调配置.md#)|查询录制回调配置|
|[UpdateLiveRecordNotifyConfig](intl.zh-CN/API参考/直播录制/更新录制回调配置.md#)|更新录制回调配置|

## 直播流管理 {#section_p4q_gz5_cfb .section}

|API|描述|
|:--|:-|
|[ForbidLiveStream](intl.zh-CN/API参考/直播流管理/禁止直播流推送.md#)|禁止直播流推送|
|[DescribeLiveStreamsBlockList](intl.zh-CN/API参考/直播流管理/查询推流黑名单列表.md#)|查询推流黑名单列表|
|[DescribeLiveStreamsControlHistory](intl.zh-CN/API参考/直播流管理/查询流控历史.md#)|查询流控历史|
|[DescribeLiveStreamsOnlineList](intl.zh-CN/API参考/直播流管理/查询推流在线列表.md#)|查询推流在线列表|
|[DescribeLiveStreamsPublishList](intl.zh-CN/API参考/直播流管理/查询推流历史.md#)|查询推流历史|
|[ResumeLiveStream](intl.zh-CN/API参考/直播流管理/恢复直播流推送.md#)|恢复直播流推送|
|[DescribeLiveStreamsFrameRateAndBitRateData](intl.zh-CN/API参考/直播流管理/查询直播流实时帧率和码率.md#)|查询直播流实时帧率和码率|
|[DescribeLiveStreamBitRateData](intl.zh-CN/API参考/直播流管理/查询直播流历史帧率和码率.md#)|查询直播流历史帧率和码率|

## 直播转码 {#section_afr_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveStreamTranscode](intl.zh-CN/API参考/直播转码/添加转码配置.md#)|添加转码配置|
|[DeleteLiveStreamTranscode](intl.zh-CN/API参考/直播转码/删除转码配置.md#)|删除转码配置|
|[DescribeLiveStreamTranscodeInfo](intl.zh-CN/API参考/直播转码/查询转码配置信息.md#)|查询转码配置信息|
|[AddCustomLiveStreamTranscode](intl.zh-CN/API参考/直播转码/添加自定义转码配置.md#)|添加自定义转码配置|
|[AddTrancodeSEI](intl.zh-CN/API参考/直播转码/添加转码SEI信息.md#)|添加转码SEI信息|

## 资源监控 {#section_pmr_gz5_cfb .section}

|API|描述|
|:--|:-|
|[DescribeLiveStreamHistoryUserNum](intl.zh-CN/API参考/资源监控/查询直播流历史在线人数.md#)|查询直播流历史在线人数|
|[DescribeLiveStreamOnlineUserNum](intl.zh-CN/API参考/资源监控/查询直播流实时在线人数.md#)|查询直播流实时在线人数|
|[DescribeLiveDomainBpsData](intl.zh-CN/API参考/资源监控/查询直播域名网络带宽监控数据.md#)|查询直播域名网络带宽监控数据|
|[DescribeLiveDomainTrafficData](intl.zh-CN/API参考/资源监控/查询直播域名网络流量监控数据.md#)|查询直播域名网络流量监控数据|
|[DescribeLiveDomainTranscodeData](intl.zh-CN/API参考/资源监控/查询直播域名转码时长数据.md#)|查询直播域名转码时长数据|
|[DescribeLiveDomainRecordData](intl.zh-CN/API参考/资源监控/查询直播域名录制时长数据.md#)|查询直播域名录制时长数据|
|[DescribeLiveDomainSnapshotData](intl.zh-CN/API参考/资源监控/查询直播域名截图张数数据.md#)|查询直播域名截图张数数据|

