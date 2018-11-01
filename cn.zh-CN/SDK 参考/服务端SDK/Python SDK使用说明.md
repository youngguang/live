# Python SDK使用说明 {#concept_ptt_myd_qfb .concept}

本文介绍Python SDK使用说明。请您按照以下步骤操作。

## 环境准备 {#section_ltx_hc2_qfb .section}

Python 2.7+

## SDK安装 {#section_blt_3c2_qfb .section}

```
sudo pip install aliyun-python-sdk-live
```

## SDK更新 {#section_pnc_jc2_qfb .section}

```
sudo pip install aliyun-python-sdk-live --upgrade
```

## SDK移除 {#section_rhd_jc2_qfb .section}

```
sudo pip uninstall aliyun-python-sdk-live
```

## 接口说明 {#section_b2h_jc2_qfb .section}

以 DescribeLiveStreamsFrameRateAndBitRateData接口为例。

以下是 SDK 中的 `DescribeLiveStreamsFrameRateAndBitRateDataRequest.py`

```
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
#
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
from aliyunsdkcore.request import RpcRequest
class DescribeLiveStreamsFrameRateAndBitRateDataRequest(RpcRequest):
    def __init__(self):
        RpcRequest.__init__(self, 'live', '2016-11-01', 'DescribeLiveStreamsFrameRateAndBitRateData','live')
    def get_SecurityToken(self):
        return self.get_query_params().get('SecurityToken')
    def set_SecurityToken(self,SecurityToken):
        self.add_query_param('SecurityToken',SecurityToken)
    def get_OwnerId(self):
        return self.get_query_params().get('OwnerId')
    def set_OwnerId(self,OwnerId):
        self.add_query_param('OwnerId',OwnerId)
    def get_DomainName(self):
        return self.get_query_params().get('DomainName')
    def set_DomainName(self,DomainName):
        self.add_query_param('DomainName',DomainName)
    def get_AppName(self):
        return self.get_query_params().get('AppName')
    def set_AppName(self,AppName):
        self.add_query_param('AppName',AppName)
    def get_StreamName(self):
        return self.get_query_params().get('StreamName')
    def set_StreamName(self,StreamName):
        self.add_query_param('StreamName',StreamName)
    def get_StartTime(self):
        return self.get_query_params().get('StartTime')
    def set_StartTime(self,StartTime):
        self.add_query_param('StartTime',StartTime)
    def get_EndTime(self):
        return self.get_query_params().get('EndTime')
    def set_EndTime(self,EndTime):
        self.add_query_param('EndTime',EndTime)
```

该文件中对于 DescribeLiveStreamsFrameRateAndBitRateDataRequest这个类，有若干组一一对应的 `get_X` 和 `set_X` 方法，分别用于设定该 API 请求的参数，具体每一个请求参数对应的意义，您可以在阿里云官网的直播 API 文档中找到。

## SDK使用 {#section_kbv_4c2_qfb .section}

以 `v20161101` 版本为例。

以调用 DescribeLiveStreamsFrameRateAndBitRateDataRequest接口为例。

```
# 引入aliyunsdkcore包
from aliyunsdkcore import client
# 入 aliyunsdklie 包
from aliyunsdklive.request.v20161101 import DescribeLiveStreamsFrameRateAndBitRateDataRequest
#初始化 clie t
# AK 和 Secrect 需要自己提供 (可以在阿里云控制台中找到)
# 以访问 cn-hangzhou region 为例
clt = client.AcsClient(AK, Secret, 'cn-hangzhou')
#构造需发起的 API 请求调用
request = DescribeLiveStreamsFrameRateAndBitRateDataRequest()
request.set_DomainName('qt1.alivecdn.com')
request.set_AppName('caster')
request.set_StreamName('cc8d5e157f5d4146afd091e246efd1f6')
# 发起请求
result = clt.do_action_with_exception(request)
# 看求结果
 result 为 请求果的 ResponseBody 字符串
print rsult
 如果您需要进一步对 result 进行处理, 您可以根据每个接口的返回格式, 进行格式化处理并进一步分析或使用
# 对于 DescribeLiveStreamsFrameRateAndBitRateDataRequest 来说, 它返回一个 json 格式的数据, 我们可以用 json 包来处理这些response
import json
x = json.loads(result)
print x['RequestId']
print x['FrameRateAndBitRateInfos']
```

