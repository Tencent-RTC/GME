# 腾讯云游戏多媒体引擎（GME）SDK

简体中文 | [English](./README.md)

[GME（Game Multimedia Engine）](https://cloud.tencent.com/product/gme) 是腾讯云提供的一站式游戏语音解决方案。本仓库（`sdk/api/gme`）是 GME SDK 对外暴露的**客户端 API 接口定义**，包含 C++、Objective-C、Java、C#（Unity）、Dart（Flutter）、TypeScript（Cocos Creator / Electron）等多语言接口声明，各语言接口在命名与调用时序上保持一致。

> 本文档对应 GME SDK 3.X 版本，接口以 C++ 头文件（`cpp/`）为准，其他语言绑定为其等价封装。

## 一、功能简介

GME（Game Multimedia Engine，游戏多媒体引擎）是腾讯云提供的一站式游戏语音解决方案，覆盖实时语音、语音消息与语音 AI 三大类能力。

- **实时语音**：支持加入、退出与快速切换语音房间，提供流畅、标准、高清三档音质；支持实时语聊与音频直播/国战语音两种场景，支持主播与观众角色切换、跨房连麦以及同进程多房间实例。
- **范围语音与 3D 音效**：支持全员、小队、主持人、范围等多种语音收发模式，结合世界坐标与队伍号实现"听声辨位"；支持 3D 空间音效与距离衰减，支持对指定成员静音。
- **音频控制与设备管理**：支持麦克风/扬声器开关与上下行控制、音量增益及单用户音量调节、耳返监听；桌面端支持设备枚举选择与设备自测，移动端支持听筒/扬声器音频路由切换；支持自定义音频采集、自定义播放渲染与 PCM 音频帧回调。
- **背景音乐与音效**：支持多音源背景音乐播放、暂停、进度跳转、变调与本地/远端音量调节；提供丰富的变声与混响特效；支持房间内音频录制与系统声音采集。
- **语音消息**：支持语音的录制、上传、下载、播放与变声播放，支持限制最大录音时长与查询语音时长。
- **语音 AI**：支持语音转文字、流式语音识别、文本翻译与文本转语音。
- **消息通道与质量监控**：支持自定义数据通道与 SEI 消息通道；提供网络质量、成员音量、频谱与说话状态等实时回调；提供日志等级/路径配置、调试仪表盘与麦克风权限查询。
- **鉴权**：支持本地计算 UserSig 鉴权码（生产环境建议在业务后台生成）。

## 二、平台支持

GME SDK 覆盖主流原生平台与游戏/应用引擎，各平台对应的接口目录如下：

| 平台 / 引擎 | 接口语言 | 本仓库接口目录 | 说明 |
| --- | --- | --- | --- |
| Windows | C++ | `cpp/` | 支持设备枚举/选择、设备热插拔、麦克风与扬声器测试、系统声音采集 |
| macOS | C++ / Objective-C | `cpp/`、`oc/` | 支持设备枚举/选择、系统声音采集 |
| iOS | Objective-C | `oc/` | 支持静音键检测、音频路由（听筒/扬声器）切换 |
| Android | Java | `java/` | 需通过 `GMESDK.setApplicationContext(context)` 设置 ApplicationContext |
| HarmonyOS | — | — | 接口随 HarmonyOS SDK 包提供 |
| Unity | C# | `unity/` | 基于 C# 封装，需在 `Update` 中调用 `Poll` 与 `UpdateSelfPosition` |
| Unreal Engine | C++ | `cpp/` | 使用 C++ 接口 |
| Flutter | Dart | `dart/` | 通过 `ITMGContext.GetInstance()` 获取实例 |
| Electron | TypeScript | `electron/` | npm 包方式集成 |
| Cocos Creator | TypeScript | `cocosCreator/` | TypeScript 接口封装 |
| Web H5 | JavaScript | — | 独立版本，接口随 Web SDK 包提供 |

### 平台能力差异

| 能力 | 说明 |
| --- | --- |
| 仅桌面端（Windows / macOS） | 麦克风/扬声器设备枚举与选择（`GetMicList` / `SelectSpeaker` 等）、设备测试（`StartMicDeviceTest` / `StartSpeakerDeviceTest`）、系统声音采集（`StartSystemAudioLoopback`）、扬声器默认设备变更事件 |
| 仅移动端（iOS / Android） | 音频路由切换（`SetAudioRoute`）、iOS 静音键检测（`ITMG_MAIN_EVENT_TYPE_IOS_MUTE_SWITCH_RESULT`）、麦克风权限查询（`CheckMicPermission`） |
| Windows 版本依赖 | 指定进程 / 指定路径的系统声音采集需 Windows 10.0.19042（20H2）及以上；x64 SDK 指定路径混音同样需该版本 |
| 服务端环境 | SDK 依据 AppID 自动选择接入点：国内站申请的 AppID 连接国内站，国际站申请的 AppID 连接国际站（`SetRegion` 已废弃） |

## 三、SDK 下载

当前 GME 3.X 最新版本为 **v3.10.0**（更新时间：2026-9-22），各平台 SDK、Sample Project 与接入文档下载地址如下：

| 平台 / 引擎 | 版本 | 更新时间 | SDK 下载 | Sample Project | 接入文档 |
| --- | --- | --- | --- | --- | --- |
| Unity | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnity_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnity_source_apiexample_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/101373) |
| Unreal Engine | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnreal_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnreal_source_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/101543) |
| Windows | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Windows/GME_Win_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Windows/GME_Win_source_apiexample_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/101546) |
| iOS | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/iOS/GME_iOS_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/iOS/GME_iOS_source_apiexample_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/118392) |
| Android | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Android/GME_Android_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Android/GME_Android_source_apiexample_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/113785) |
| HarmonyOS | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/OHOS/GME_OHOS_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/OHOS/GME_OHOS_source_apiexample_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/132379) |
| macOS | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Mac/GME_Mac_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Mac/GME_Mac_source_testdemo_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/132667) |
| Electron | v3.10.0 | 2026-9-22 | [下载（npm）](https://www.npmjs.com/package/gme-electron-sdk-v3) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_Electron_demo_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/132664) |
| Flutter | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEFlutter_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEFlutter_Demo_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/131915) |
| Cocos Creator | v3.10.0 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_CocosCreator_sdk_3.10.0.698.zip) | [下载](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_CocosCreator_source_exapmle_3.10.0.698.zip) | [快速入门](https://cloud.tencent.com/document/product/607/131919) |
| Web H5 | v5.6.1.53 | 2026-9-22 | [下载](https://dl.gmertc.com/gme/Custom/Web/GME_Web_SDK_5.6.1.53.zip) | [下载](https://dl.gmertc.com/gme/Custom/Web/GME_Web_Demo_5.6.1.53.zip) | [快速入门](https://cloud.tencent.com/document/product/607/138988) |

### 下载与接入说明

- **最新版本**：完整下载列表与历史版本发布日志参见 [SDK 3.X 下载指引](https://cloud.tencent.com/document/product/607/124288) 与 [产品动态](https://cloud.tencent.com/document/product/607/41876)。
- **新手入门**：首次使用请先参见 [新手指引](https://cloud.tencent.com/document/product/607/51583) 开通服务并获取 `AppID` 与 `Key`。
- **版本升级**：从 2.X 升级到 3.X 请参考 [SDK 2.X 升级 3.X 指引](https://cloud.tencent.com/document/product/607/103879)。
- **接入与体验**：接入流程参见 [快速接入 SDK](https://cloud.tencent.com/document/product/607/88893)；运行 Sample Project 参见 [快速接入 Sample Project](https://cloud.tencent.com/document/product/607/89954)。
- **合规使用**：使用前请阅读 [SDK 个人信息保护规则](https://cloud.tencent.com/document/product/607/59299)，并按 [SDK 合规接入详细操作指引](https://cloud.tencent.com/document/product/607/81880)、[SDK 接入使用说明](https://cloud.tencent.com/document/product/607/81874) 合规接入。
- **产品功能与错误码**：[产品功能](https://cloud.tencent.com/document/product/607/77642)、[客户端 API](https://cloud.tencent.com/document/product/607/15232)、[错误码](https://cloud.tencent.com/document/product/607/15173)。
