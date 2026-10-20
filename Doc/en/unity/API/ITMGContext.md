# ITMGContext

Copyright \(c\) 2025 Tencent. All rights reserved.

Module:   TMGContext@GMESDK

Function: Tencent Cloud GME Main Functional Interface.

## ITMGContext

| Function List | Description |
| --- | --- |
| [GetInstance](#getinstance) | Retrieve the GME SDK instance \(singleton pattern\). |
| [SetLibraryPath](#setlibrarypath) | Specify the path for Native library files. |
| [CreateSubInstance](#createsubinstance) | Create a GME sub-instance. |
| [DestroySubInstance](#destroysubinstance) | Destroy a sub-instance. |
| [SetRegion](#setregion) | Configure access point \(deprecated\). |
| [Init](#init) | Initialize the GME SDK. |
| [Poll](#poll) | Process event callbacks. |
| [Pause](#pause) | Pause system. |
| [Resume](#resume) | Resume system. |
| [Uninit](#uninit) | Uninitialize the GME SDK. |
| [SetScene](#setscene) | Configure application scenario. |
| [SetAudioRole](#setaudiorole) | Switch user role. |
| [SetRangeAudioMode](#setrangeaudiomode) | Set range audio mode. |
| [SetRangeAudioTeamID](#setrangeaudioteamid) | Set TeamID for range audio. |
| [EnterRoom](#enterroom) | Join a voice room. |
| [ExitRoom](#exitroom) | Leave a voice room. |
| [IsRoomEntered](#isroomentered) | Check room entry status. |
| [SetLogLevel](#setloglevel) | Configure log level. |
| [SetLogPath](#setlogpath) | Specify log file path. |
| [GetLogPath](#getlogpath) | Retrieve log file path. |
| [GetSDKVersion](#getsdkversion) | Retrieve GME SDK version. |
| [SetAppVersion](#setappversion) | Set app version number. |
| [ShowDebugView](#showdebugview) | Display dashboard. |
| [GetRoom](#getroom) | Retrieve room-related class instance. |
| [GetPttCtrl](#getpttctrl) | Retrieve offline voice class instance. |
| [GetAudioCtrl](#getaudioctrl) | Retrieve audio control class instance. |
| [GetAudioEffectCtrl](#getaudioeffectctrl) | Retrieve audio effect control class instance. |
| [SetRecvMixStreamCount](#setrecvmixstreamcount) | Set maximum mixed stream count. |
| [SetAdvanceParams](#setadvanceparams) | Configure advanced parameters. |
| [GetAdvanceParams](#getadvanceparams) | Retrieve advanced parameter values. |
| [CheckMicPermission](#checkmicpermission) | Check microphone permission. |

## GetInstance

**Retrieve the GME SDK instance \(singleton pattern\).**

This is the core entry point for the GME SDK and should be called first.

## SetLibraryPath

```csharp
void SetLibraryPath(string libPath);
```

**Specify the path for Native library files**

Customize the path for Native library files. This method is only effective on Android and must be called before [`GetInstance`](#getinstance). By default, you do not need to call this method.

## CreateSubInstance

**Create a GME sub-instance.**

Call this method to create a `TMGContext` sub-instance. You can initialize the sub-instance with the same or different `appid` and `userid` as the main instance, and join a specific audio room.

## DestroySubInstance

```csharp
void DestroySubInstance(ITMGContext subInstance);
```

**Destroy a sub-instance.**

Call this method from the main instance to destroy a sub-instance.

| Parameter | Description |
| --- | --- |
| subInstance | Sub-room instance. |

## SetRegion

```csharp
void SetRegion(string region);
```

**Configure access point \(deprecated\).**

Normally, you do not need to call this method manually. The SDK automatically selects the access point based on the AppID. If the AppID is for the China site, it connects to the China environment; if for the International site, it connects to the International environment.

| Parameter | Description |
| --- | --- |
| region | Access point. Options: "REGION\_CHN" \(China site\), "REGION\_INTERNATIONAL" \(International site\). Call this method before [Init](#init). |

## Init

```csharp
int Init(string appId, string userID);
```

**Initialize the GME SDK.**

Call this method to initialize the SDK before using any GME features.

| Parameter | Description |
| --- | --- |
| appId | GME application AppID from Tencent Cloud. |
| userID | Current user's UserID \(username\), UTF-8 encoded, up to 127 characters. |

## Poll

**Process event callbacks.**

`Poll` acts as the GME message pump. Your application must call `Poll` periodically to process event callbacks. If `Poll` is not called, the SDK will not function properly.

## Pause

**Pause system.**

When the system triggers a pause event, notify the engine by calling `Pause`. If you do not need to play room audio in the background, use `Pause` to suspend the GME service.

## Resume

**Resume system.**

When the system resumes, call `Resume` to notify the engine. `Resume` only restores real-time voice functionality.

## Uninit

**Uninitialize the GME SDK.**

After using GME features, call this method to release resources. If your game account is bound to a UserID, switch accounts by uninitializing GME and then initializing with the new UserID.

## SetScene

```csharp
int SetScene(ITMG_APP_SCENE scene);
```

**Configure application scenario.**

The default scenario is voice chat. A single room supports up to 300 concurrent users, with up to 50 users speaking simultaneously. Suitable for scenarios such as voice chat, online Werewolf, team gaming, and similar use cases.

If a room exceeds 300 users, call this method to switch to the audio live streaming scenario before calling [`EnterRoom`](#enterroom).

## SetAudioRole

```csharp
int SetAudioRole(ITMG_AUDIO_MEMBER_ROLE role);
```

**Switch user role.**

Switch between Host and Audience roles.

In interactive live streaming or large-scale voice scenarios, only the Host can publish audio streams, while the Audience can only receive streams. If an Audience needs to publish audio, call this method to switch their role to Host.

## SetRangeAudioMode

```csharp
int SetRangeAudioMode(ITMG_RANGE_AUDIO_MODE rangeAudioMode);
```

**Set range audio mode.**

Call this method before joining a room to set the audio mode for your next room entry.

After joining a room, call this method to change the current user's audio mode immediately.

After leaving a room, this parameter does not reset automatically. If you use this method, call it before each [`EnterRoom`](#enterroom) to set the audio mode.

## SetRangeAudioTeamID

```csharp
int SetRangeAudioTeamID(int teamID);
```

**Set TeamID for range audio.**

Set the team number before joining a room to affect your next room entry.

After joining a room, call this method to change the team number immediately.

After leaving a room, TeamID does not reset to 0 automatically. If you use this audio mode, call this method before each [`EnterRoom`](#enterroom) to set the TeamID.

If you re-enter a room after leaving, set the team number after receiving the exit callback.

## EnterRoom

```csharp
int EnterRoom(string roomId, ITMGRoomType roomType, string userSig);
```

**Join a voice room.**

Join the specified voice room. This method is asynchronous. The result is notified via the [`ITMG_MAIN_EVENT_TYPE`](Type-Definitions.md#itmg_main_event_type) `ITMG_MAIN_EVENT_TYPE_ENTER_ROOM` event.

| Parameter | Description |
| --- | --- |
| roomId | Voice room ID, up to 64 characters. |
| roomType | Room type. |
| userSig | User authentication information. |

## ExitRoom

**Leave a voice room.**

Call this method to leave the current room. This method is asynchronous. If the return value is `AV_OK`, the asynchronous call succeeded. The result is notified via the [`ITMG_MAIN_EVENT_TYPE`](Type-Definitions.md#itmg_main_event_type) `ITMG_MAIN_EVENT_TYPE_EXIT_ROOM` event.

> **Note**
> 
> If your application needs to enter a room immediately after leaving, you do not need to wait for the [`ExitRoom`](#exitroom) callback. Simply call the method directly.

## IsRoomEntered

**Check room entry status.**

Call this method to determine if you are already in a room. Returns a boolean value.

## SetLogLevel

```csharp
int SetLogLevel(int levelWrite, int levelPrint);
```

**Configure log level.**

Set the log level. It is recommended to use the default level. Call this method before [`Init`](#init).

| Parameter | Description |
| --- | --- |
| levelPrint | Log print level. |
| levelWrite | Log file write level. |

## SetLogPath

```csharp
int SetLogPath(string logDir);
```

**Specify log file path.**

Set the log file storage path. Call this method before [`Init`](#init).

| Parameter | Description |
| --- | --- |
| logDir | Log file storage path. |

## GetLogPath

**Retrieve log file path.**

## GetSDKVersion

**Retrieve GME SDK version.**

## SetAppVersion

```csharp
void SetAppVersion(string appVersion);
```

**Set app version number.**

The application can report its version number to the GME SDK for internal tracking.

| Parameter | Description |
| --- | --- |
| appVersion | Application version information. |

## ShowDebugView

```csharp
int ShowDebugView(bool show);
```

**Display dashboard.**

The dashboard is a floating view that displays status statistics and event messages, useful for debugging.

| Parameter | Description |
| --- | --- |
| show | Whether to display the dashboard. |

## GetRoom

**Retrieve room-related class instance.**

## GetPttCtrl

**Retrieve offline voice class instance.**

## GetAudioCtrl

**Retrieve audio control class instance.**

## GetAudioEffectCtrl

**Retrieve audio effect control class instance.**

## SetRecvMixStreamCount

```csharp
int SetRecvMixStreamCount(int count);
```

**Set maximum mixed stream count.**

Set the maximum number of mixed streams. Call this method before joining a room.

| Parameter | Description |
| --- | --- |
| count | Maximum number of mixed streams. |

## SetAdvanceParams

```csharp
int SetAdvanceParams(string key, string value);
```

**Configure advanced parameters.**

| Parameter | Description |
| --- | --- |
| key | Parameter name. |
| value | Parameter value. |

## GetAdvanceParams

```csharp
string GetAdvanceParams(string key);
```

**Retrieve advanced parameter values.**

## CheckMicPermission

**Check microphone permission.**