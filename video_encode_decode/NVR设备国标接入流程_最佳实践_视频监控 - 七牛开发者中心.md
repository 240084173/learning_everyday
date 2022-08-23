# NVR设备国标接入流程_最佳实践_视频监控 - 七牛开发者中心
            NVR设备国标接入流程\_最佳实践\_视频监控 - 七牛开发者中心     

Toggle navigation [](javascript:;)[![](https://developer.qiniu.com/assets/logo-white-b90d685a6b146884636382426d11b7236f5f7ca1c5dfafdb6fa777a0f976fc1f.png)
开发者中心](/)

*   [产品与服务](javascript:;)
    *   [对象存储](/kodo)
    *   [私有云存储](/kodoe)
    *   [智能日志管理平台](/insight)
    *   [CDN](/fusion)
    *   [智能多媒体服务](/dora)
    *   [直播云](/pili)
    *   [实时音视频](/rtc)
    *   [SSL 证书服务](/ssl)
    *   [云主机](/qvm)
    *   [专有云计算](/qec)
    *   [内容审核](/censor)
    *   [视频监控](/qvs)
    *   [云短信](/sms)
    *   [机器数据分析平台](/express)
    *   [边缘加速](/PCDN)
    *   [即时通讯](/IM)
    *   [互动白板](/whiteboard)
    *   [全站加速](/dcdn)
    *   [低代码](/lowcode)
*   [SDK & 工具](javascript:;)
    *   [官方 SDK](/sdk#official-sdk)
    *   [社区 SDK](/sdk#community-sdk)
    *   [开发者工具](/sdk#official-tool)
    *   [社区插件](/sdk#community-plugin)
*   [解决方案](https://www.qiniu.com/solutions)
*   [FAQ](/faq)
*   [技术支持](https://support.qiniu.com/)

*   [官网](https://www.qiniu.com/)
*   [管理控制台](https://portal.qiniu.com/)
*   [更多](javascript:;)
    *   [官网](https://www.qiniu.com/)
    *   [管理控制台](https://portal.qiniu.com/)
*   [SDK & 工具](/sdk)
*   [解决方案](https://www.qiniu.com/solutions)
*   [输入搜索的关键字](/search)
*   [技术支持](https://support.qiniu.com/)
*   [](javascript:;)
    *   [退出当前帐号](https://sso.qiniu.com/signout)
*   [登录](https://sso.qiniu.com?client_id=qauxtCZX9RGtu5wVf4E8qrruem5Ko2I0ZFzuHV4uIYzgAioQVhjE5QAZuLP8Lh2o&redirect_url=https://developer.qiniu.com)
*   [注册](https://portal.qiniu.com/signup)

 

### [视频监控](/qvs)

*   [使用文档](javascript:;)
    1.  [产品简介](javascript:;)
        1.  [产品概述](/qvs/6753/qvs-product-overview)
        2.  [功能概述](/qvs/6754/qvs-functions-overview)
        3.  [产品优势](/qvs/6755/qvs-product-advantage)
        4.  [计费方式](/qvs/6893/qvs-billing-way)
        5.  [名词解释](/qvs/6757/qvs-noun-explanation)
    2.  [快速入门](/qvs/6763/qvs-quick-start)
    3.  [使用指南](javascript:;)
        1.  [空间管理](/qvs/6784/namespace-management)
        2.  [视频流管理](/qvs/6785/video-streaming-management)
        3.  [设备管理](/qvs/7026/equipment-control)
            1.  [语音对讲](/qvs/8324/voice-intercom)
            2.  [本地录像回放](/qvs/7405/Local-video-playback)
            3.  [PTZ管理](/qvs/7406/ptz-management)
            4.  [报警事件通知](/qvs/7999/alarm-event-notification)
            5.  [HTTPS配置](/qvs/6925/qvs-https-configuration)
        4.  [模板管理](javascript:;)
            1.  [录制模板](/qvs/6789/recording-the-template)
            2.  [截图模板](/qvs/6790/screenshot-of-the-template)

*   [API 文档](javascript:;)
    1.  [API概述](/qvs/6706/summary-of-the-api)
    2.  [调用方式](javascript:;)
        1.  [错误响应](/qvs/10238/qvs-error-response)
        2.  [HTTP Headers](/qvs/6709/qvs-http-headers)
        3.  [鉴权机制](/qvs/6713/authentication)
        4.  [请求结构](/qvs/6711/request)
    3.  [空间管理相关接口](javascript:;)
        1.  [消息回调](/qvs/10240/the-message-callback)
        2.  [创建空间](/qvs/6726/create-namespace)
        3.  [删除空间](/qvs/6727/delete-namespace)
        4.  [更新空间](/qvs/6728/update-namespace)
        5.  [查询空间信息](/qvs/6729/query-namespace)
        6.  [获取空间列表](/qvs/6730/list-namespace)
        7.  [禁用空间](/qvs/6759/disable-the-space)
        8.  [启用空间](/qvs/6760/enable-the-space)
    4.  [流管理相关接口](javascript:;)
        1.  [使用流接口必读](/qvs/11878/use-the-stream-interface-is-required)
        2.  [创建流](/qvs/6734/create-flow)
        3.  [删除流](/qvs/6735/delete-flow)
        4.  [更新流](/qvs/6758/update-the-flow)
        5.  [查询流信息](/qvs/6736/query-information-flow)
        6.  [获取流列表](/qvs/6737/query-list-flow)
        7.  [获取流地址](/qvs/6740/obtain-flow-address)
            1.  [静态模式](/qvs/6800/static-model)
            2.  [动态模式](/qvs/6801/dynamic-model)
        8.  [启用流](/qvs/6739/enable-the-flow)
        9.  [禁用流](/qvs/6738/disable-the-flow)
        10.  [停止推流](/qvs/6849/stop-using-flow)
        11.  [查询推流记录](/qvs/6742/query-flow-records)
    5.  [设备管理相关接口](javascript:;)
        1.  [一对多语音对讲](/qvs/10744/one-to-many-voice-intercom)
        2.  [私有信令透传](/qvs/10757/gb-private-signaling-passthrough)
        3.  [创建设备](/qvs/6896/create-device)
        4.  [批量创建设备](/qvs/10086/batch-create-device)
        5.  [获取批次列表](/qvs/10170/get-batch-list)
        6.  [获取批次设备信息](/qvs/10160/export-batch-equipment)
        7.  [删除批次](/qvs/10171/batch-remove-devices)
        8.  [删除设备](/qvs/6898/Delete-device)
        9.  [更新设备](/qvs/6899/update-the-device)
        10.  [查询设备信息](/qvs/6901/Query-device-information)
        11.  [获取设备列表](/qvs/6902/Query-device-list)
        12.  [获取通道列表](/qvs/6906/query-channel-list)
        13.  [删除通道](/qvs/7120/delete-the-channel)
        14.  [启动设备拉流](/qvs/6907/start-device)
        15.  [停止设备拉流](/qvs/6908/stop-device)
        16.  [语音对讲](/qvs/8158/voice-call)
        17.  [停止语音对讲](/qvs/11860/stop-voice-intercom)
        18.  [获取设备地理位置](/qvs/10243/get-to-location)
    6.  [模板管理相关接口](javascript:;)
        1.  [创建模板](/qvs/6721/create-template)
        2.  [删除模板](/qvs/6722/delete-template)
        3.  [更新模板](/qvs/6723/modify-the-template)
        4.  [查询模板信息](/qvs/6724/template-information)
        5.  [获取模板列表](/qvs/6725/list-template)
    7.  [域名管理相关接口](javascript:;)
        1.  [更新域名信息](/qvs/7317/update-domain)
        2.  [删除域名](/qvs/6904/delete-domain)
        3.  [修改域名时间戳防盗链配置](/qvs/10481/the-domain-name-configuration)
        4.  [创建域名](/qvs/6903/create-domain)
        5.  [获取域名列表](/qvs/6905/domain-name-list)
        6.  [获取证书列表](/qvs/6891/to-obtain-a-list-certificate)
        7.  [域名对应的HTTPs开关](/qvs/6890/open-the-domain-name-corresponding-https-switch)
        8.  [获取域名信息](/qvs/6917/domain-information)
    8.  [录制管理相关接口](javascript:;)
        1.  [启动按需录制](/qvs/6743/start-record-stream)
        2.  [停止按需录制](/qvs/6744/stop-record-stream)
        3.  [查询录制记录](/qvs/6745/query-recordhistories)
        4.  [删除录制片段](/qvs/6746/delete-recorded-fragments)
        5.  [录制视频片段合并](/qvs/7140/record-video-clips)
        6.  [录制回放](/qvs/6747/recording-playback)
        7.  [按需截图](/qvs/6748/start-snapshot)
        8.  [删除截图](/qvs/7109/deleted-screenshots)
        9.  [获取截图列表](/qvs/6749/list-stream-snapshots)
        10.  [获取直播封面截图](/qvs/6814/the-cover-for-screenshots)
    9.  [本地录像回放相关接口](javascript:;)
        1.  [本地录像下载](/qvs/10172/local-video-download)
        2.  [本地录像回放控制](/qvs/8405/local-video-playback-control)
        3.  [查询本地录像列表](/qvs/7112/query-local-video-list)
        4.  [本地录像上传云端](/qvs/7765/uploaded-to-the-cloud)
        5.  [终止本地录像上传云端](/qvs/7766/stop-uploaded-to-the-cloud)
    10.  [PTZ相关接口](/qvs/7289/ptz-related-interface)
        1.  [云台控制](/qvs/7290/ptz-control)
        2.  [变焦控制](/qvs/7292/zoom-control)
        3.  [光圈控制](/qvs/7291/aperture-control)
        4.  [预置位控制](/qvs/7293/set-the-preset-position)
        5.  [获取预置位列表](/qvs/7295/get-prepared-list)
    11.  [国标报警相关接口](javascript:;)
        1.  [获取国标报警事件列表](/qvs/7775/gb-alarm-events-list)
    12.  [数据统计相关接口](javascript:;)
        1.  [查询流量数据](/qvs/6855/query-the-network-traffic-data)
        2.  [查询带宽数据](/qvs/6856/query-data-bandwidth)
        3.  [推流路数统计](/qvs/7768/the-flow-route-statistics)
        4.  [查询国标接入设备数](/qvs/8748/gb-devicecount)

*   [SDK 下载](javascript:;)
    1.  [推流端SDK](/qvs/8736/push-the-sdk)
    2.  [服务端SDK](javascript:;)
        1.  [PHP SDK](/qvs/8744/php-sdk-qvs)
        2.  [Python SDK](/qvs/8745/python-sdk-for-qvs)
        3.  [C# SDK](/qvs/12162/qvs-c-sdk)
        4.  [Java SDK](/qvs/6923/qvs-java-sdk)
        5.  [Go SDK](/qvs/6924/qvs-go-sdk)
    3.  [播放端SDK](/qvs/7924/play-the-sdk)

*   [最佳实践](javascript:;)
    1.  [设备本地录像上传云端存储](/qvs/8425/local-video-upload-the-cloud)
    2.  [配置域名的CNAME](/qvs/8746/configure-cname)
    3.  [利用国标告警大幅减少云存储成本](/qvs/10235/using-national-standard-warning-greatly-reduces-costs-of-cloud-storage)
    4.  [RTMP接入流程](/qvs/7452/rtmp-access-process)
    5.  [摄像头国标接入流程](/qvs/7448/gb-access-process)
    6.  [NVR设备国标接入流程](/qvs/7451/nvr-gb-access-process)
    7.  [按需拉流使用介绍](/qvs/7703/on-demand-pull-flow-introduced)
    8.  [低延时实时直播-webrtc接入流程](/qvs/7812/low-latency-will-broadcast-live-webrtc-access-process)

*   [故障排查](javascript:;)
    1.  [国标接入问题排查](/qvs/7447/gb-access-problems)
    2.  [QVS Q&A](/qvs/11880/qvs-q-a)

*   [常见问题](/faq?space=qvs)

[视频监控](/qvs) > 最佳实践 > NVR设备国标接入流程

NVR设备国标接入流程
===========

最近更新时间: 2021-08-13 12:04:48

**本文简述了使用国标协议接入NVR设备的配置流程，以及接入流程演示视频**。  
NVR（网络视频存储）设备接入QVS过程与摄像头接入流程基本类似，都先要在QVS平台下已经创建好的国标类型的空间下先添加设备，此时设备类型需要选择为**平台**。然后在设备端进行国标注册操作，注册成功后，在QVS控制台中可以查看接入的NVR设备状态。

**NVR设备接入配置示范**
===============

**操作步骤：** 
----------

1.首先需要在七牛云视频监控产品portal上查询已经添加好的对应的配置信息，如尚未创建请参考[快速入门](https://developer.qiniu.io/qvs/manual/6763/qvs-quick-start)。  
2.登录到NVR设备的配置页面中，找到国标接入配置页面。  
3.将对应信息配置到NVR设备上、启用国标保存后，该设备将进行注册接入。  
4.请确保nvr各个通道下,视频编码格式为h264,码流控制/码率类型选择“可变码率”;音频编码格式为aac,或者g711-alaw。

**海康设备国标接入配置示范**
----------------

[![](https://dn-odum9helk.qbox.me/FtHAVF3IcsxMox-1tDtx9d6yp49q)
](https://dn-odum9helk.qbox.me/FtHAVF3IcsxMox-1tDtx9d6yp49q)  
_配置参数说明：_

| 参数 | 说明 |
| --- | --- |
| 平台接入方式 | 选择28181 |
| 本地SIP端口 | 由于设备默认的本地Sip端口号5060,可能会被局域网屏蔽，建议修改为5061、5062等其他端口号 |
| SIP服务器ID | 填入视频监控平台（QVS）提供的SIP服务器ID |
| SIP服务器域 | SIP服务器ID的前10位 |
| SIP服务地址 | 填入视频监控平台（QVS）提供的SIP服务器IP |
| SIP服务器端口 | 填入视频监控平台（QVS）提供的SIP服务器端口号 |
| SIP用户认证ID | 填入视频监控平台（QVS）中创建对应的设备时输入或自动生成的设备国标ID，NVR设备的国标ID，11-13位为118 |
| 密码 | 填入视频监控平台（QVS）中创建对应的设备时输入的密码 |

**海康NVR设备需要为该设备下，接入的摄像头对应通道分配视频通道编码ID（摄像头设备的国标ID）**  
NVR设备下的视频通道编码，可自行分配，不重复即可，11-13位可填132；可参照下面的示例进行配置，示例如下：  
D1:31011500991320000001  
D2:31011500991320000002  
D3:31011500991320000003  
…按顺序排列填写即可（NVR接入了多少个摄像头填写多少个通道即可）  
[![](https://dn-odum9helk.qbox.me/Fl0tQq_4nwq6UqNW3attGYSxr3-t)
](https://dn-odum9helk.qbox.me/Fl0tQq_4nwq6UqNW3attGYSxr3-t)

**大华设备国标接入配置示范**
----------------

[![](https://dn-odum9helk.qbox.me/FkllVbXux5M0LlZ92y6duf2Npv6_)
](https://dn-odum9helk.qbox.me/FkllVbXux5M0LlZ92y6duf2Npv6_)  
_配置参数说明：_

| 参数 | 说明 |
| --- | --- |
| SIP服务器编号 | 填入视频监控平台（QVS）提供的SIP服务器ID |
| SIP域 | SIP服务器ID的前10位 |
| SIP服务IP | 填入视频监控平台（QVS）提供的SIP服务器IP |
| SIP服务器端口 | 填入视频监控平台（QVS）提供的SIP服务器端口号 |
| 设备编号 | 填入视频监控平台（QVS）中创建对应的设备时输入或自动生成的设备国标ID，NVR设备的国标ID，11-13位为118 |
| 密码 | 填入视频监控平台（QVS）中创建对应的设备时输入的密码 |
| 本地SIP端口 | 由于设备默认的本地SIP端口号5060,可能会被局域网屏蔽，建议修改为5061、5062等其他端口号 |

**视频卡顿/拉流失败时，建议的参数配置**
----------------------

当同一个网络内接入的设备过多时或者摄像头所处的网络环境波动较大时，会由于网络带宽的限制导致视频卡顿或者拉流失败，以海康nvr(录像机)为例，建议的参数配置  
  
  
[![](https://dn-odum9helk.qbox.me/Fp0b-JRnEzcV0z_oEhVCSkYRjc8u)
](https://dn-odum9helk.qbox.me/Fp0b-JRnEzcV0z_oEhVCSkYRjc8u)

**接入流程演示**
==========

以下演示的是海康NVR接入

  

以上内容是否对您有帮助？

文档反馈 (如有产品使用问题，请 [提交工单](https://support.qiniu.com/tickets/category))

 

提交

*   [NVR设备接入配置示范](#1)
*   [接入流程演示](#2)

 [![](https://dn-odum9helk.qbox.me/rightbanner)](https://marketing.qiniu.com/activity/qvm0rmbv2?entry=dev-right-button "免费注册") 

![](https://developer.qiniu.com/assets/icon-sevice-21342418ba5b3d3a9ba87d3ef1df87fabd3a1c59a9e76a8b71df63efdbfbfef1.png)
 服务•咨询 

*   ![](https://developer.qiniu.com/assets/icon-advisory-e829965a1f7c283cba59344ad4c41e0908992c23334d3fbeeda4fd3b99464f80.jpg)
     售前  立即咨询
*   ![](https://developer.qiniu.com/assets/icon-workorder-ad2a429d75a4db924c06a60628e110d1e031f77957156fc6c9c7dc6249b9a736.jpg)
     售后  [提交工单](https://support.qiniu.com/tickets/category)

[![](https://developer.qiniu.com/assets/close-c80c279cfed4ad83fa45163d69624d1cfacc5a42b9338006dd1a26e4730e5e1e.png)
](javascript:;)

回到顶部

×

#### 产品及服务咨询

提交成功！

提交失败，稍后重试！

此表单仅用于产品及服务售前咨询（您也可以拨打400-808-9176转2）  
如有售后技术咨询，请[提交工单](https://support.qiniu.com/tickets/category)

 

咨询内容\*

请填写咨询内容

最多可输入255字

姓名\*

请填写姓名

公司名称

省份\*

北京市天津市河北省山西省内蒙古自治区辽宁省吉林省黑龙江省上海市江苏省浙江省安徽省福建省江西省山东省河南省湖北省湖南省广东省广西壮族自治区海南省重庆市四川省贵州省云南省西藏自治区陕西省甘肃省青海省宁夏回族自治区新疆维吾尔自治区香港特别行政区澳门特别行政区台湾

联系电话\*

请以正确的格式填写联系电话

电子邮箱\*

请填写电子邮箱

提交

© 2022 七牛云

*   [七牛官网](http://www.qiniu.com)
*   [开发者平台](https://portal.qiniu.com)
*   [问答社区](https://segmentfault.com/qiniu)
*   [技术支持](https://support.qiniu.com)
*   [服务状态](https://status.qiniu.com/)
*   [七牛标识](/brand)

[沪公网安备 31011502000961 号](http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31011502000961) [沪 ICP 备 11037377 号-5](http://www.beian.miit.gov.cn)

*   [](javascript:;)
    
    ![](https://developer.qiniu.com/assets/weixin-qrcode-e4ddfa8a1a16b96c60e4b671b676dfd168ab4f91b5a700a755dde294347fc0f0.png)
    

![](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)