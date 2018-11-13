# 直播API概述 {#concept_mmr_bhl_bfb .concept}

请确保在使用这些接口前，已充分了解视频直播产品说明和收费方式。

当前Live Open API版本号为：2016-11-01。

## 术语表 {#section_n5h_bz5_cfb .section}

## 业务限制资源规格限制说明 {#section_arw_bz5_cfb .section}

见[附录](../../../../cn.zh-CN/旧版API 参考/附录.md#)

## 直播截图 {#section_m3m_2z5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveAppSnapshotConfig](cn.zh-CN/API 参考/直播截图/添加截图配置.md#)|添加截图配置|
|[DeleteLiveAppSnapshotConfig](cn.zh-CN/API 参考/直播截图/删除截图配置.md#)|删除截图配置|
|[DescribeLiveSnapshotConfig](cn.zh-CN/API 参考/直播截图/查询域名下的截图配置.md#)|查询域名下的截图配置|
|[DescribeLiveStreamSnapshotInfo](cn.zh-CN/API 参考/直播截图/查询截图信息.md#)|查询截图信息|
|[UpdateLiveAppSnapshotConfig](cn.zh-CN/API 参考/直播截图/更新截图配置.md#)|更新截图配置|

## 直播拉流 {#section_c5n_gz5_cfb .section}

|API|描述|
|:--|:-|
|[DeleteLivePullStreamInfoConfig](cn.zh-CN/API 参考/直播拉流/删除拉流.md#)|删除拉流|
|[AddLivePullStreamInfoConfig](cn.zh-CN/API 参考/直播拉流/添加拉流.md#)|添加拉流|
|[DescribeLivePullStreamConfig](cn.zh-CN/API 参考/直播拉流/查询拉流信息.md#)|查询拉流信息|

## 直播审核 {#section_hn4_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveSnapshotDetectPornConfig](cn.zh-CN/API 参考/直播审核/添加审核配置.md#)|添加审核配置|
|[AddLiveDetectNotifyConfig](cn.zh-CN/API 参考/直播审核/添加审核回调.md#)|添加审核回调|
|[DescribeLiveSnapshotDetectPornConfig](cn.zh-CN/API 参考/直播审核/查询审核配置.md#)|查询审核配置|
|[DescribeLiveDetectNotifyConfig](cn.zh-CN/API 参考/直播审核/查询审核回调.md#)|查询审核回调|
|[UpdateLiveSnapshotDetectPornConfig](cn.zh-CN/API 参考/直播审核/更新审核配置.md#)|更新审核配置|
|[UpdateLiveDetectNotifyConfig](cn.zh-CN/API 参考/直播审核/更新审核回调.md#)|更新审核回调|
|[DeleteLiveSnapshotDetectPornConfig](cn.zh-CN/API 参考/直播审核/删除审核配置.md#)|删除审核配置|
|[DeleteLiveDetectNotifyConfig](cn.zh-CN/API 参考/直播审核/删除审核回调.md#)|删除审核回调|

## 状态通知 {#section_o1p_gz5_cfb .section}

|API|描述|
|:--|:-|
|[SetLiveStreamsNotifyUrlConfig](cn.zh-CN/API 参考/状态通知/设置NotifyURL.md#)|设置NotifyURL|
|[DescribeLiveStreamsNotifyUrlConfig](cn.zh-CN/API 参考/状态通知/查询NotifyURL.md#)|查询NotifyURL|
|[DeleteLiveStreamsNotifyUrlConfig](cn.zh-CN/API 参考/状态通知/删除NotifyURL.md#)|删除NotifyURL|

## 直播转点播 {#section_avp_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveRecordVodConfig](cn.zh-CN/API 参考/直播转点播/添加直转点配置.md#)|添加直转点配置|
|[DescribeLiveRecordVodConfigs](cn.zh-CN/API 参考/直播转点播/查询直转点配置.md#)|查询直转点配置|
|[DeleteLiveRecordVodConfig](cn.zh-CN/API 参考/直播转点播/删除直转点配置.md#)|删除直转点配置|

## 直播录制 {#section_nfq_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveAppRecordConfig](cn.zh-CN/API 参考/直播录制/添加APP录制配置.md#)|添加APP录制配置|
|[DeleteLiveAppRecordConfig](cn.zh-CN/API 参考/直播录制/删除APP录制配置.md#)|删除APP录制配置|
|[DescribeLiveRecordConfig](cn.zh-CN/API 参考/直播录制/查询域名下录制配置列表.md#)|查询域名下录制配置列表|
|[DescribeLiveStreamRecordContent](cn.zh-CN/API 参考/直播录制/查询录制内容.md#)|查询录制内容|
|[CreateLiveStreamRecordIndexFiles](cn.zh-CN/API 参考/直播录制/创建录制索引文件.md#)|创建录制索引文件|
|[DescribeLiveStreamRecordIndexFile](cn.zh-CN/API 参考/直播录制/查询单个录制索引文件.md#)|查询单个录制索引文件|
|[DescribeLiveStreamRecordIndexFiles](cn.zh-CN/API 参考/直播录制/查询录制索引文件.md#)|查询录制索引文件|
|[AddLiveRecordNotifyConfig](cn.zh-CN/API 参考/直播录制/添加录制回调配置.md#)|添加录制回调配置|
|[DeleteLiveRecordNotifyConfig](cn.zh-CN/API 参考/直播录制/删除录制回调配置.md#)|删除录制回调配置|
|[DescribeLiveRecordNotifyConfig](cn.zh-CN/API 参考/直播录制/查询录制回调配置.md#)|查询录制回调配置|
|[UpdateLiveRecordNotifyConfig](cn.zh-CN/API 参考/直播录制/更新录制回调配置.md#)|更新录制回调配置|

## 直播流管理 {#section_p4q_gz5_cfb .section}

|API|描述|
|:--|:-|
|[ForbidLiveStream](cn.zh-CN/API 参考/直播流管理/禁止直播流推送.md#)|禁止直播流推送|
|[DescribeLiveStreamsBlockList](cn.zh-CN/API 参考/直播流管理/查询推流黑名单列表.md#)|查询推流黑名单列表|
|[DescribeLiveStreamsControlHistory](cn.zh-CN/API 参考/直播流管理/查询流控历史.md#)|查询流控历史|
|[DescribeLiveStreamsOnlineList](cn.zh-CN/API 参考/直播流管理/查询推流在线列表.md#)|查询推流在线列表|
|[DescribeLiveStreamsPublishList](cn.zh-CN/API 参考/直播流管理/查询推流历史.md#)|查询推流历史|
|[ResumeLiveStream](cn.zh-CN/API 参考/直播流管理/恢复直播流推送.md#)|恢复直播流推送|
|[DescribeLiveStreamsFrameRateAndBitRateData](cn.zh-CN/API 参考/直播流管理/查询直播流实时帧率和码率.md#)|查询直播流实时帧率和码率|
|[DescribeLiveStreamBitRateData](cn.zh-CN/API 参考/直播流管理/查询直播流历史帧率和码率.md#)|查询直播流历史帧率和码率|

## 导播服务 {#section_nwq_gz5_cfb .section}

|API|描述|
|:--|:-|
| [CreateCaster](cn.zh-CN/导播服务/API参考/创建导播台.md#)|创建导播台|
|[AddCasterLayout](cn.zh-CN/导播服务/API参考/添加布局.md#)|添加导播台布局|
|[AddCasterVideoResource](cn.zh-CN/导播服务/API参考/添加视频源.md#)|添加视频源|
|[AddCasterEpisode](cn.zh-CN/导播服务/API参考/添加导播台节目.md#)|添加导播台节目|
|[AddCasterComponent](cn.zh-CN/导播服务/API参考/添加组件.md#)|添加组件|
|[AddCasterProgram](cn.zh-CN/导播服务/API参考/添加导播台节目单.md#)|添加导播台节目单|
|[AddCasterEpisodeGroup](cn.zh-CN/导播服务/API参考/添加导播台节目.md#)|添加导播台节目列表|
|[AddCasterEpisodeGroupContent](cn.zh-CN/导播服务/API参考/添加节目单列表内容.md#)|添加节目单列表内容|
|[CallBack](cn.zh-CN/导播服务/API参考/添加回调.md#)|添加回调|
|[CopyCaster](cn.zh-CN/导播服务/API参考/复制导播台.md#)|复制导播台|
|[CopyCasterSceneConfig](cn.zh-CN/导播服务/API参考/复制场景配置.md#)|复制场景配置|
|[DeleteCaster](cn.zh-CN/导播服务/API参考/删除导播台.md#)|删除导播台|
|[DeleteCasterLayout](cn.zh-CN/导播服务/API参考/删除布局.md#)|删除布局|
|[DeleteCasterVideoResource](cn.zh-CN/导播服务/API参考/删除视频源.md#)|删除视频资源|
|[DeleteCasterComponent](cn.zh-CN/导播服务/API参考/删除组件.md#)|删除组件|
|[DeleteCasterEpisode](cn.zh-CN/导播服务/API参考/删除导播台节目.md#)|删除导播台节目|
|[DeleteCasterProgram](cn.zh-CN/导播服务/API参考/删除导播台节目单.md#)|删除导播台节目单|
|[DeleteCasterEpisodeGroup](cn.zh-CN/导播服务/API参考/删除导播台节目列表.md#)|删除导播台节目列表|
|[DeleteCasterSceneConfig](cn.zh-CN/导播服务/API参考/删除导播台场景配置.md#)|删除导播台场景配置|
| [DescribeCasterConfig](cn.zh-CN/导播服务/API参考/查询导播台配置信息.md#) |查询导播台配置|
| [DescribeCasterLayouts](cn.zh-CN/导播服务/API参考/查询布局列表.md#)|查询导播台布局列表|
| [DescribeCasters](cn.zh-CN/导播服务/API参考/查询导播台列表.md#) |查询导播台列表|
| [DescribeCasterScenes](cn.zh-CN/导播服务/API参考/查询导播台场景列表.md#)|查询导播台场景列表|
| [DescribeCasterStreamUrl](cn.zh-CN/导播服务/API参考/查询导播台流地址.md#)|查询导播台流地址|
|[DescribeCasterVideoResources](cn.zh-CN/导播服务/API参考/查询视频源.md#)|查询视频源|
|[DescribeCasterProgram](cn.zh-CN/导播服务/API参考/查询导播台节目单.md#)|查询导播台节目单|
|[DescribeCasterComponents](cn.zh-CN/导播服务/API参考/查询组件列表.md#)|查询组件列表|
|[DescribeCasterSceneAudio](cn.zh-CN/导播服务/API参考/查询场景音频配置.md#)|查询场景音频配置|
|[DescribeCasterChannels](cn.zh-CN/导播服务/API参考/查询导播台通道.md#)|查询导播台通道|
| [EffectCasterUrgent](cn.zh-CN/导播服务/API参考/切换备播.md#)|切换备播|
| [EffectCasterVideoResource](cn.zh-CN/导播服务/API参考/更新备播.md#)|更新备播片|
| [ModifyCasterLayout](cn.zh-CN/导播服务/API参考/修改布局.md#)|修改布局|
| [ModifyCasterVideoResource](cn.zh-CN/导播服务/API参考/修改视频源.md#)|修改视频源|
| [ModifyCasterComponent](cn.zh-CN/导播服务/API参考/修改组件.md#)|修改组件|
|[ModifyCasterEpisode](cn.zh-CN/导播服务/API参考/修改导播台节目.md#)|修改导播台节目|
| [ModifyCasterProgram](cn.zh-CN/导播服务/API参考/修改导播台节目单.md#)|修改导播台节目单|
| [SetCasterConfig](cn.zh-CN/导播服务/API参考/配置导播台.md#) |配置导播台|
| [SetCasterSceneConfig](cn.zh-CN/导播服务/API参考/设置场景配置.md#)|设置场景配置|
|[SetCasterChannel](cn.zh-CN/导播服务/API参考/设置导播台通道.md#)|设置导播台通道|
|[StartCasterScene](cn.zh-CN/导播服务/API参考/启动场景.md#) |启动场景|
|[StartCaster](cn.zh-CN/导播服务/API参考/启动导播台.md#)|启动导播台|
| [StopCasterScene](cn.zh-CN/导播服务/API参考/停止场景.md#) |停止场景|
|[StopCaster](cn.zh-CN/导播服务/API参考/停止导播台.md#)|停止导播台|
| [UpdateCasterSceneConfig](cn.zh-CN/导播服务/API参考/更新导播场景配置.md#)|更新导播场景配置|
|[UpdateCasterSceneAudio](cn.zh-CN/导播服务/API参考/更新场景音频配置.md#) |更新场景音频配置|

## 直播转码 {#section_afr_gz5_cfb .section}

|API|描述|
|:--|:-|
|[AddLiveStreamTranscode](cn.zh-CN/API 参考/直播转码/添加转码配置.md#)|添加转码配置|
|[DeleteLiveStreamTranscode](cn.zh-CN/API 参考/直播转码/删除转码配置.md#)|删除转码配置|
|[DescribeLiveStreamTranscodeInfo](cn.zh-CN/API 参考/直播转码/查询转码配置信息.md#)|查询转码配置信息|
|[AddCustomLiveStreamTranscode](cn.zh-CN/API 参考/直播转码/添加自定义转码配置.md#)|添加自定义转码配置|
|[AddTrancodeSEI](cn.zh-CN/API 参考/直播转码/添加转码SEI信息.md#)|添加转码SEI信息|

## 资源监控 {#section_pmr_gz5_cfb .section}

|API|描述|
|:--|:-|
|[DescribeLiveStreamHistoryUserNum](cn.zh-CN/API 参考/资源监控/查询直播流历史在线人数.md#)|查询直播流历史在线人数|
|[DescribeLiveStreamOnlineUserNum](cn.zh-CN/API 参考/资源监控/查询直播流实时在线人数.md#)|查询直播流实时在线人数|
|[DescribeLiveDomainBpsData](cn.zh-CN/API 参考/资源监控/查询直播域名网络带宽监控数据.md#)|查询直播域名网络带宽监控数据|
|[DescribeLiveDomainTrafficData](cn.zh-CN/API 参考/资源监控/查询直播域名网络流量监控数据.md#)|查询直播域名网络流量监控数据|
|[DescribeLiveDomainTranscodeData](cn.zh-CN/API 参考/资源监控/查询直播域名转码时长数据.md#)|查询直播域名转码时长数据|
|[DescribeLiveDomainRecordData](cn.zh-CN/API 参考/资源监控/查询直播域名录制时长数据.md#)|查询直播域名录制时长数据|
|[DescribeLiveDomainSnapshotData](cn.zh-CN/API 参考/资源监控/查询直播域名截图张数数据.md#)|查询直播域名截图张数数据|

