# Tencent Cloud Game Multimedia Engine (GME) SDK

[简体中文](./README-zh_CN.md) | English

[GME (Game Multimedia Engine)](https://cloud.tencent.com/product/gme) is a one-stop voice solution for games provided by Tencent Cloud. This repository (`sdk/api/gme`) contains the **client-side API definitions** exposed by the GME SDK, including C++, Objective-C, Java, C# (Unity), Dart (Flutter) and TypeScript (Cocos Creator / Electron) declarations. All language bindings share consistent naming and calling sequences.

> This document applies to GME SDK 3.X. The C++ headers (`cpp/`) are the source of truth; other language bindings are equivalent wrappers.

## 1. Features

GME (Game Multimedia Engine) is a one-stop voice solution for games provided by Tencent Cloud, covering real-time voice, voice messaging and voice AI.

- **Real-time Voice**: Join, exit and quickly switch between voice rooms, with three audio quality profiles (fluency, standard and high quality). Supports both real-time chat and audio live/national-war voice scenarios, anchor/audience role switching, cross-room connection, and multiple room instances within a single process.
- **Range Voice & 3D Sound Effects**: Multiple audio send/receive modes (all members, team, host, proximity, etc.) combined with world coordinates and team IDs to enable positional voice. Supports 3D spatial audio with distance attenuation and per-user muting.
- **Audio Control & Device Management**: Enable/disable microphone and speaker, upstream/downstream control, volume gain and per-user volume adjustment, in-ear monitoring. Desktop platforms support device enumeration, selection and self-test; mobile platforms support earpiece/speaker audio route switching. Custom audio capture, custom audio rendering and PCM audio frame callbacks are also supported.
- **Background Music & Sound Effects**: Multi-track background music playback with pause, seek, pitch shifting and local/remote volume adjustment. A rich set of voice changing and reverb effects. In-room audio recording and system audio loopback capture.
- **Voice Messaging**: Record, upload, download, play and play with voice effects. Supports limiting the maximum recording duration and querying voice duration.
- **Voice AI**: Speech-to-text, streaming speech recognition, text translation and text-to-speech.
- **Messaging Channel & Quality Monitoring**: Custom data channel and SEI message channel. Real-time callbacks for network quality, member volume, audio spectrum and speaking (VAD) status. Log level/path configuration, debug dashboard and microphone permission query.
- **Authentication**: Supports local UserSig generation (generating UserSig on the business backend is recommended for production).

## 2. Platform Support

The GME SDK covers major native platforms and game/application engines. The corresponding API directory for each platform is listed below.

| Platform / Engine | Language | API Directory | Notes |
| --- | --- | --- | --- |
| Windows | C++ | `cpp/` | Device enumeration/selection, device hot-plug, microphone and speaker test, system audio loopback |
| macOS | C++ / Objective-C | `cpp/`, `oc/` | Device enumeration/selection, system audio loopback |
| iOS | Objective-C | `oc/` | Mute switch detection, audio route switching (earpiece/speaker) |
| Android | Java | `java/` | Requires `GMESDK.setApplicationContext(context)` to set the ApplicationContext |
| HarmonyOS | — | — | APIs shipped with the HarmonyOS SDK package |
| Unity | C# | `unity/` | C# wrapper; `Poll` and `UpdateSelfPosition` must be called in `Update` |
| Unreal Engine | C++ | `cpp/` | Uses the C++ API |
| Flutter | Dart | `dart/` | Obtain the instance via `ITMGContext.GetInstance()` |
| Electron | TypeScript | `electron/` | Integrated as an npm package |
| Cocos Creator | TypeScript | `cocosCreator/` | TypeScript API wrapper |
| Web H5 | JavaScript | — | Separate version; APIs shipped with the Web SDK package |

### Platform Differences

| Capability | Description |
| --- | --- |
| Desktop only (Windows / macOS) | Microphone/speaker device enumeration and selection (`GetMicList` / `SelectSpeaker`, etc.), device test (`StartMicDeviceTest` / `StartSpeakerDeviceTest`), system audio loopback (`StartSystemAudioLoopback`), speaker default device changed event |
| Mobile only (iOS / Android) | Audio route switching (`SetAudioRoute`), iOS mute switch detection (`ITMG_MAIN_EVENT_TYPE_IOS_MUTE_SWITCH_RESULT`), microphone permission query (`CheckMicPermission`) |
| Windows version requirement | System audio loopback for a specified process or path requires Windows 10.0.19042 (20H2) or later; path-based loopback on the x64 SDK requires the same version |
| Server environment | The SDK automatically selects the access point based on the AppID: AppIDs registered on the Chinese site connect to the domestic environment, while AppIDs registered on the international site connect to the international environment (`SetRegion` is deprecated) |

## 3. SDK Download

The latest GME 3.X release is **v3.10.0** (updated: 2026-9-22). Download links for each platform's SDK, Sample Project and integration guide are listed below.

| Platform / Engine | Version | Updated | SDK | Sample Project | Integration Guide |
| --- | --- | --- | --- | --- | --- |
| Unity | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnity_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnity_source_apiexample_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/101373) |
| Unreal Engine | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnreal_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEUnreal_source_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/101543) |
| Windows | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Windows/GME_Win_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Windows/GME_Win_source_apiexample_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/101546) |
| iOS | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/iOS/GME_iOS_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/iOS/GME_iOS_source_apiexample_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/118392) |
| Android | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Android/GME_Android_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Android/GME_Android_source_apiexample_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/113785) |
| HarmonyOS | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/OHOS/GME_OHOS_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/OHOS/GME_OHOS_source_apiexample_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/132379) |
| macOS | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Mac/GME_Mac_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Mac/GME_Mac_source_testdemo_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/132667) |
| Electron | v3.10.0 | 2026-9-22 | [Download (npm)](https://www.npmjs.com/package/gme-electron-sdk-v3) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_Electron_demo_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/132664) |
| Flutter | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEFlutter_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GMEFlutter_Demo_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/131915) |
| Cocos Creator | v3.10.0 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_CocosCreator_sdk_3.10.0.698.zip) | [Download](https://dl.gmertc.com/gme/GME3.10.0/Other/GME_CocosCreator_source_exapmle_3.10.0.698.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/131919) |
| Web H5 | v5.6.1.53 | 2026-9-22 | [Download](https://dl.gmertc.com/gme/Custom/Web/GME_Web_SDK_5.6.1.53.zip) | [Download](https://dl.gmertc.com/gme/Custom/Web/GME_Web_Demo_5.6.1.53.zip) | [Quick Start](https://cloud.tencent.com/document/product/607/138988) |

> Note: The documentation links above point to the Tencent Cloud documentation site, where some pages are available in Chinese only.

### Download & Integration Notes

- **Latest Version**: For the complete download list and historical release notes, see [SDK 3.X Download Guide](https://cloud.tencent.com/document/product/607/124288) and [Release Notes](https://cloud.tencent.com/document/product/607/41876).
- **Getting Started**: If this is your first time using the SDK, follow the [Getting Started Guide](https://cloud.tencent.com/document/product/607/51583) to activate the service and obtain your `AppID` and `Key`.
- **Version Upgrade**: To upgrade from 2.X to 3.X, refer to the [SDK 2.X to 3.X Upgrade Guide](https://cloud.tencent.com/document/product/607/103879).
- **Integration & Demo**: See [Quick SDK Integration](https://cloud.tencent.com/document/product/607/88893) for the integration flow, and [Quick Sample Project Integration](https://cloud.tencent.com/document/product/607/89954) to run the Sample Project.
- **Compliance**: Read the [SDK Personal Information Protection Rules](https://cloud.tencent.com/document/product/607/59299) before use, and integrate in compliance with the [SDK Compliance Integration Guide](https://cloud.tencent.com/document/product/607/81880) and [SDK Integration Instructions](https://cloud.tencent.com/document/product/607/81874).
- **Features & Error Codes**: [Product Features](https://cloud.tencent.com/document/product/607/77642), [Client APIs](https://cloud.tencent.com/document/product/607/15232), [Error Codes](https://cloud.tencent.com/document/product/607/15173).
