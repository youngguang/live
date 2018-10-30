# API概述 {#concept_60293_zh .concept}

导播服务提供了一系列API接口，可以分为导播台创建与配置、视频内容编辑、视频内容输出、查询和管理等五大类。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/60293/cn_zh/1517206351001/003.png)

在创建好导播台实例之后，通过使用API接口也能够快速的接入并使用服务，如上图。

1.  创建（CreateCaster）和配置导播台（SetCasterConfig）
2.  添加导播视频资源（AddCasterVideoResource）
3.  添加导播台布局（AddCasterLayout）
4.  启动导播台（StartCaster）
5.  停止导播台（StopCaster）

## 导播API列表 { .section}

|API|描述|
|:--|:-|
| [CreateCaster](../../../../cn.zh-CN/导播服务/API参考/创建导播台.md#)|创建导播台|
|[AddCasterLayout](../../../../cn.zh-CN/导播服务/API参考/添加布局.md#)|添加导播台布局|
|[AddCasterVideoResource](../../../../cn.zh-CN/导播服务/API参考/添加视频源.md#)|添加视频源|
|[AddCasterEpisode](cn.zh-CN/导播服务/API参考/添加导播台节目.md#)|添加导播台节目|
|[AddCasterComponent](../../../../cn.zh-CN/导播服务/API参考/添加组件.md#)|添加组件|
|[AddCasterProgram](cn.zh-CN/导播服务/API参考/添加导播台节目单.md#)|添加导播台节目单|
|[AddCasterEpisodeGroup](cn.zh-CN/导播服务/API参考/添加导播台节目.md#)|添加导播台节目列表|
|[AddCasterEpisodeGroupContent](cn.zh-CN/导播服务/API参考/添加节目单列表内容.md#)|添加节目单列表内容|
|[CallBack](../../../../cn.zh-CN/导播服务/API参考/添加回调.md#)|添加回调|
|[CopyCaster](../../../../cn.zh-CN/导播服务/API参考/复制导播台.md#)|复制导播台|
|[CopyCasterSceneConfig](../../../../cn.zh-CN/导播服务/API参考/复制场景配置.md#)|复制场景配置|
|[DeleteCaster](../../../../cn.zh-CN/导播服务/API参考/删除导播台.md#)|删除导播台|
|[DeleteCasterLayout](../../../../cn.zh-CN/导播服务/API参考/删除布局.md#)|删除布局|
|[DeleteCasterVideoResource](../../../../cn.zh-CN/导播服务/API参考/删除视频源.md#)|删除视频资源|
|[DeleteCasterComponent](../../../../cn.zh-CN/导播服务/API参考/删除组件.md#)|删除组件|
|[DeleteCasterEpisode](cn.zh-CN/导播服务/API参考/删除导播台节目.md#)|删除导播台节目|
|[DeleteCasterProgram](cn.zh-CN/导播服务/API参考/删除导播台节目单.md#)|删除导播台节目单|
|[DeleteCasterEpisodeGroup](cn.zh-CN/导播服务/API参考/删除导播台节目列表.md#)|删除导播台节目列表|
|[DeleteCasterSceneConfig](cn.zh-CN/导播服务/API参考/删除导播台场景配置.md#)|删除导播台场景配置|
| [DescribeCasterConfig](../../../../cn.zh-CN/.md#) |查询导播台配置|
| [DescribeCasterLayouts](../../../../cn.zh-CN/导播服务/API参考/查询布局列表.md#)|查询导播台布局列表|
| [DescribeCasters](../../../../cn.zh-CN/导播服务/API参考/查询导播台列表.md#) |查询导播台列表|
| [DescribeCasterScenes](../../../../cn.zh-CN/导播服务/API参考/查询导播台场景列表.md#)|查询导播台场景列表|
| [DescribeCasterStreamUrl](../../../../cn.zh-CN/导播服务/API参考/查询导播台流地址.md#)|查询导播台流地址|
|[DescribeCasterVideoResources](../../../../cn.zh-CN/导播服务/API参考/查询视频源.md#)|查询视频源|
|[DescribeCasterProgram](cn.zh-CN/导播服务/API参考/查询导播台节目单.md#)|查询导播台节目单|
|[DescribeCasterComponents](../../../../cn.zh-CN/导播服务/API参考/查询组件列表.md#)|查询组件列表|
|[DescribeCasterSceneAudio](cn.zh-CN/导播服务/API参考/查询场景音频配置.md#)|查询场景音频配置|
|[DescribeCasterChannels](cn.zh-CN/.md#)|查询导播台通道|
| [EffectCasterUrgent](../../../../cn.zh-CN/导播服务/API参考/切换备播.md#)|切换备播|
| [EffectCasterVideoResource](../../../../cn.zh-CN/导播服务/API参考/更新备播.md#)|更新备播片|
| [ModifyCasterLayout](../../../../cn.zh-CN/导播服务/API参考/修改布局.md#)|修改布局|
| [ModifyCasterVideoResource](../../../../cn.zh-CN/导播服务/API参考/修改视频源.md#)|修改视频源|
| [ModifyCasterComponent](../../../../cn.zh-CN/导播服务/API参考/修改组件.md#)|修改组件|
|[ModifyCasterEpisode](cn.zh-CN/导播服务/API参考/修改导播台节目.md#)|修改导播台节目|
| [ModifyCasterProgram](cn.zh-CN/导播服务/API参考/修改导播台节目单.md#)|修改导播台节目单|
| [SetCasterConfig](../../../../cn.zh-CN/导播服务/API参考/配置导播台.md#) |配置导播台|
| [SetCasterSceneConfig](../../../../cn.zh-CN/导播服务/API参考/设置场景配置.md#)|设置场景配置|
|[SetCasterChannel](cn.zh-CN/导播服务/API参考/设置导播台通道.md#)|设置导播台通道|
|[StartCasterScene](../../../../cn.zh-CN/导播服务/API参考/启动场景.md#) |启动场景|
|[StartCaster](../../../../cn.zh-CN/导播服务/API参考/启动导播台.md#)|启动导播台|
| [StopCasterScene](../../../../cn.zh-CN/导播服务/API参考/停止场景.md#) |停止场景|
|[StopCaster](../../../../cn.zh-CN/导播服务/API参考/停止导播台.md#)|停止导播台|
| [UpdateCasterSceneConfig](../../../../cn.zh-CN/导播服务/API参考/更新导播场景配置.md#)|更新导播场景配置|
|[UpdateCasterSceneAudio](cn.zh-CN/导播服务/API参考/更新场景音频配置.md#) |更新场景音频配置|

