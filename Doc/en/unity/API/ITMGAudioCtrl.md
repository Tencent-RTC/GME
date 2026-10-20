# ITMGAudioCtrl

Copyright \(c\) 2025 Tencent. All rights reserved.

Module:   TMGAudioCtrl@GMESDK

Function: Tencent Cloud GME audio control function interfaces.

## ITMGAudioFrameCallback

| Function List | Description |
| --- | --- |
| [OnCapturedAudioFrame](#oncapturedaudioframe) | Callback for locally captured audio data after preprocessing. |
| [OnLocalProcessedAudioFrame](#onlocalprocessedaudioframe) | Callback for locally captured audio data after preprocessing, audio effects, and background music mixing. |
| [OnPlayAudioFrame](#onplayaudioframe) | Audio data for each remote user before mixing. |
| [OnMixedPlayAudioFrame](#onmixedplayaudioframe) | Callback for mixed audio data of all streams before system playback. |
| [OnMixedAllAudioFrame](#onmixedallaudioframe) | Audio data after mixing all streams in the SDK \(including captured and playback audio\). |
| [EnableMic](#enablemic) | Enable or disable the microphone. |
| [GetMicState](#getmicstate) | Get microphone status. |
| [EnableSpeaker](#enablespeaker) | Enable or disable the speaker. |
| [GetSpeakerState](#getspeakerstate) | Get speaker status. |
| [EnableAudioCaptureDevice](#enableaudiocapturedevice) | Enable capture device. |
| [IsAudioCaptureDeviceEnabled](#isaudiocapturedeviceenabled) | Get capture device status. |
| [EnableAudioPlayDevice](#enableaudioplaydevice) | Enable or disable playback device. |
| [IsAudioPlayDeviceEnabled](#isaudioplaydeviceenabled) | Get playback device status. |
| [EnableAudioSend](#enableaudiosend) | Enable or disable audio upstream. |
| [IsAudioSendEnabled](#isaudiosendenabled) | Get audio upstream status. |
| [EnableAudioRecv](#enableaudiorecv) | Enable or disable audio downstream. |
| [IsAudioRecvEnabled](#isaudiorecvenabled) | Get audio downstream status. |
| [SetMicVolume](#setmicvolume) | Set microphone gain. |
| [GetMicVolume](#getmicvolume) | Get microphone gain. |
| [SetSpeakerVolume](#setspeakervolume) | Set speaker gain. |
| [GetSpeakerVolume](#getspeakervolume) | Get speaker gain. |
| [SetSpeakerVolumeByUserID](#setspeakervolumebyuserid) | Set speaker gain for a user in the room. |
| [GetSpeakerVolumeByUserID](#getspeakervolumebyuserid) | Get speaker gain for a user in the room. |
| [EnableLoopBack](#enableloopback) | Enable or disable loopback \(monitoring\). |
| [SetLoopBackVolume](#setloopbackvolume) | Set loopback volume. |
| [AddAudioBlackList](#addaudioblacklist) | Mute a user in the room. |
| [RemoveAudioBlackList](#removeaudioblacklist) | Unmute a user in the room. |
| [IsUserIDInAudioBlackList](#isuseridinaudioblacklist) | Check if a user is muted. |
| [InitSpatializer](#initspatializer) | Initialize 3D audio processor. |
| [EnableSpatializer](#enablespatializer) | Enable or disable 3D audio effects. |
| [IsEnableSpatializer](#isenablespatializer) | Get current 3D audio effect status. |
| [GetMicListCount](#getmiclistcount) | Get microphone device count \(desktop only\). |
| [GetMicList](#getmiclist) | List microphone devices \(desktop only\). |
| [SelectMic](#selectmic) | Select microphone device \(desktop only\). |
| [GetCurrentMic](#getcurrentmic) | Get current microphone device \(desktop only\). |
| [GetSpeakerListCount](#getspeakerlistcount) | Get speaker device count \(desktop only\). |
| [GetSpeakerList](#getspeakerlist) | List speaker devices \(desktop only\). |
| [SelectSpeaker](#selectspeaker) | Select speaker device \(desktop only\). |
| [GetCurrentSpeaker](#getcurrentspeaker) | Get current speaker device \(desktop only\). |
| [EnableCustomAudioCapture](#enablecustomaudiocapture) | Enable custom audio capture mode. |
| [SetAudioRoute](#setaudioroute) | Set audio route. |
| [SendCustomAudioData](#sendcustomaudiodata) | Send custom captured audio data to the SDK. |
| [EnableCustomAudioRendering](#enablecustomaudiorendering) | Enable custom audio playback. |
| [GetCustomAudioRenderingFrame](#getcustomaudiorenderingframe) | Retrieve playable audio data. |
| [TrackingVolume](#trackingvolume) | Enable volume callback. |
| [StopTrackingVolume](#stoptrackingvolume) | Disable volume callback. |
| [GetMicLevel](#getmiclevel) | Get real-time microphone volume. |
| [GetSpeakerLevel](#getspeakerlevel) | Get real-time speaker volume. |
| [GetSendStreamLevel](#getsendstreamlevel) | Get real-time upstream audio volume. |
| [GetRecvStreamLevel](#getrecvstreamlevel) | Get real-time downstream audio volume for other users in the room. |
| [StartMicDeviceTest](#startmicdevicetest) | Start microphone test \(desktop only\). |
| [StopMicDeviceTest](#stopmicdevicetest) | Stop microphone test \(desktop only\). |
| [StartSpeakerDeviceTest](#startspeakerdevicetest) | Start speaker test \(desktop only\). |
| [StopSpeakerDeviceTest](#stopspeakerdevicetest) | Stop speaker test \(desktop only\). |
| [SetAudioFrameCallback](#setaudioframecallback) | Set custom audio data callback. |

## OnCapturedAudioFrame

```csharp
void OnCapturedAudioFrame(TMGAudioFrame frame);
```

**Callback for locally captured audio data after preprocessing.**

Once you set the custom audio data callback, the SDK returns the captured and preprocessed audio data \(ANS, AEC, AGC\) in PCM format through this interface.

- Each callback delivers a fixed 0.02s audio frame in PCM format.
- To calculate the byte frame length: `sample rate × time frame length × channel count × sample bit width`.
- For the default GME recording format \(48000 Hz, mono, 16-bit\), the byte frame length is `48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes`.

| Parameter | Description |
| --- | --- |
| frame | Audio frame in PCM format. |

> **Note**
> 
> 1. Avoid time-consuming operations in this callback. The SDK processes audio frames every 20ms; processing longer than 20ms may cause audio issues.
> 2. The audio data is readable and writable. You can synchronously modify it within the callback, but ensure your processing is efficient.
> 3. The returned audio data is preprocessed \(ANS, AEC, AGC\) and does **not** include background music, audio effects, or reverb. Latency is low.

## OnLocalProcessedAudioFrame

```csharp
void OnLocalProcessedAudioFrame(TMGAudioFrame frame);
```

**Callback for locally captured audio data after preprocessing, audio effects, and background music mixing.**

Once you set the custom audio data callback, the SDK returns the captured and processed audio data \(preprocessing, audio effects, background music mixing\) in PCM format through this interface, before network encoding.

- Each callback delivers a fixed 0.02s audio frame in PCM format.
- To calculate the byte frame length: `sample rate × time frame length × channel count × sample bit width`.
- For the default GME recording format \(48000 Hz, mono, 16-bit\), the byte frame length is `48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes`.

| Parameter | Description |
| --- | --- |
| frame | Audio frame in PCM format. |

> **Note**
> 
> 1. Avoid time-consuming operations in this callback. The SDK processes audio frames every 20ms; processing longer than 20ms may cause audio issues.
> 2. The audio data is readable and writable. You can synchronously modify it within the callback, but ensure your processing is efficient.
> 
> > The returned data includes preprocessing \(ANS, AEC, AGC\), audio effects, and background music mixing. Latency is higher than OnCapturedAudioFrame.

## OnPlayAudioFrame

```csharp
void OnPlayAudioFrame(TMGAudioFrame frame, string userID);
```

**Audio data for each remote user before mixing.**

Once you set the custom audio data callback, the SDK returns the original audio data for each remote user, before mixing, in PCM format through this interface.

- Each callback delivers a fixed 0.02s audio frame in PCM format.
- To calculate the byte frame length: `sample rate × time frame length × channel count × sample bit width`.
- For the default GME recording format \(48000 Hz, mono, 16-bit\), the byte frame length is `48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes`.

| Parameter | Description |
| --- | --- |
| frame | Audio frame in PCM format. |
| userId | User identifier. |

> **Note**
> 
> The returned audio data is read-only and cannot be modified.

## OnMixedPlayAudioFrame

```csharp
void OnMixedPlayAudioFrame(TMGAudioFrame frame);
```

**Callback for mixed audio data of all streams before system playback.**

Once you set the custom audio data callback, the SDK returns the mixed audio data of all streams to be played, before submitting to system playback, in PCM format through this interface.

- Each callback delivers a fixed 0.02s audio frame in PCM format.
- To calculate the byte frame length: `sample rate × time frame length × channel count × sample bit width`.
- For the default GME recording format \(48000 Hz, mono, 16-bit\), the byte frame length is `48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes`.

| Parameter | Description |
| --- | --- |
| frame | Audio frame in PCM format. |

> **Note**
> 
> 1. Avoid time-consuming operations in this callback. The SDK processes audio frames every 20ms; processing longer than 20ms may cause audio issues.
> 2. The audio data is readable and writable. You can synchronously modify it within the callback, but ensure your processing is efficient.
> 3. The callback returns mixed audio data for all streams to be played, but does not include loopback audio.

## OnMixedAllAudioFrame

```csharp
void OnMixedAllAudioFrame(TMGAudioFrame frame);
```

**Audio data after mixing all streams in the SDK \(including captured and playback audio\).**

Once you set the custom audio data callback, the SDK mixes all captured and playback audio data and returns it in PCM format through this interface, for custom recording.

- Each callback delivers a fixed 0.02s audio frame in PCM format.
- To calculate the byte frame length: `sample rate × time frame length × channel count × sample bit width`.
- For the default GME recording format \(48000 Hz, mono, 16-bit\), the byte frame length is `48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes`.

| Parameter | Description |
| --- | --- |
| frame | Audio frame in PCM format. |

> **Note**
> 
> 1. This callback returns mixed audio from all SDK sources, including local audio after 3A preprocessing, effects overlay, background music mixing, and all remote audio, but excludes loopback audio.
> 2. The returned audio data cannot be modified.

## EnableMic

```csharp
int EnableMic(bool enable);
```

**Enable or disable the microphone.**

Use this interface to enable or disable the microphone and send audio to the room. Call it **after receiving the room entry success event**. By default, the microphone is disabled when joining a room.

EnableMic\(boolean\) = EnableAudioCaptureDevice\(boolean\) + EnableAudioSend\(boolean\).

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## GetMicState

**Get microphone status.**

Use this interface to query the microphone status. Returns 0 if the microphone is disabled, 1 if enabled.

## EnableSpeaker

```csharp
int EnableSpeaker(bool enable);
```

**Enable or disable the speaker.**

Use this interface to enable or disable the speaker and receive remote audio streams. Call it **after receiving the room entry success event**. By default, the speaker is disabled when joining a room.

EnableSpeaker\(boolean\) = EnableAudioPlayDevice\(boolean\) + EnableAudioRecv\(boolean\).

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## GetSpeakerState

**Get speaker status.**

Use this interface to query the speaker status. Returns 0 if the speaker is disabled, 1 if enabled.

## EnableAudioCaptureDevice

```csharp
int EnableAudioCaptureDevice(bool enable);
```

**Enable capture device.**

Use this interface to enable or disable the capture device. Call it **after receiving the room entry success event**. By default, the capture device is disabled when joining a room.

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## IsAudioCaptureDeviceEnabled

**Get capture device status.**

Use this interface to query the capture device status.

## EnableAudioPlayDevice

```csharp
int EnableAudioPlayDevice(bool enable);
```

**Enable or disable playback device.**

Use this interface to enable or disable the playback device. Call it **after receiving the room entry success event**. By default, the playback device is disabled when joining a room.

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## IsAudioPlayDeviceEnabled

**Get playback device status.**

Use this interface to query the playback device status.

## EnableAudioSend

```csharp
int EnableAudioSend(bool enable);
```

**Enable or disable audio upstream.**

Use this interface to enable or disable audio upstream. Call it after receiving the room entry success event. This controls whether captured audio is sent to remote users. If the capture device is enabled, audio is sent; if the capture device is not enabled, there will still be no sound. For capture device control, see [EnableAudioCaptureDevice](#enableaudiocapturedevice).

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## IsAudioSendEnabled

**Get audio upstream status.**

Use this interface to query the audio upstream status.

## EnableAudioRecv

```csharp
int EnableAudioRecv(bool enable);
```

**Enable or disable audio downstream.**

Use this interface to enable or disable audio downstream. Call it after receiving the room entry success event. This controls whether to receive audio from remote users. If the playback device is enabled, audio from other users in the room is played; if the playback device is not enabled, no sound will be heard. For playback device control, see [EnableAudioPlayDevice](#enableaudioplaydevice).

| Parameter | Description |
| --- | --- |
| enable | true: enable  false: disable. |

## IsAudioRecvEnabled

**Get audio downstream status.**

Use this interface to query the audio downstream status.

## SetMicVolume

```csharp
int SetMicVolume(int volume);
```

**Set microphone gain.**

Use this interface to set microphone gain.

| Parameter | Description |
| --- | --- |
| volume | Gain value, range \[0, 200\], 100 is default \(no gain or reduction\). |

## GetMicVolume

**Get microphone gain.**

Retrieve the microphone gain set via [SetMicVolume](#setmicvolume).

## SetSpeakerVolume

```csharp
int SetSpeakerVolume(int volume);
```

**Set speaker gain.**

Use this interface to set speaker gain.

| Parameter | Description |
| --- | --- |
| volume | Gain value, range \[0, 200\], 100 is default \(no gain or reduction\). |

## GetSpeakerVolume

**Get speaker gain.**

Retrieve the speaker gain set via [SetSpeakerVolume](#setspeakervolume).

## SetSpeakerVolumeByUserID

```csharp
int SetSpeakerVolumeByUserID(string userID, int volume);
```

**Set speaker gain for a user in the room.**

| Parameter | Description |
| --- | --- |
| userID | User ID. |
| volume | Gain value, range \[0, 200\], 100 is default \(no gain or reduction\). |

## GetSpeakerVolumeByUserID

```csharp
int GetSpeakerVolumeByUserID(string userID);
```

**Get speaker gain for a user in the room.**

Retrieve the gain set via [SetSpeakerVolumeByUserID](#setspeakervolumebyuserid).

| Parameter | Description |
| --- | --- |
| userID | User ID. |

## EnableLoopBack

```csharp
int EnableLoopBack(bool enable);
```

**Enable or disable loopback \(monitoring\).**

| Parameter | Description |
| --- | --- |
| enable | Enable loopback or not. |

## SetLoopBackVolume

```csharp
int SetLoopBackVolume(int volume);
```

**Set loopback volume.**

Use this interface to set loopback volume.

| Parameter | Description |
| --- | --- |
| volume | Volume value, range \[0, 200\], 100 is default \(no gain or reduction\). |

## AddAudioBlackList

```csharp
int AddAudioBlackList(string userID);
```

**Mute a user in the room.**

Add a user to the audio blacklist. Their voice will not be received locally, but this does not affect other users. Returns 0 on success.

| Parameter | Description |
| --- | --- |
| userID | User ID. |

## RemoveAudioBlackList

```csharp
int RemoveAudioBlackList(string userID);
```

**Unmute a user in the room.**

Remove a user from the audio blacklist. Returns 0 on success.

| Parameter | Description |
| --- | --- |
| userID | User ID. |

## IsUserIDInAudioBlackList

```csharp
bool IsUserIDInAudioBlackList(string userID);
```

**Check if a user is muted.**

| Parameter | Description |
| --- | --- |
| userID | User ID. |

## InitSpatializer

```csharp
int InitSpatializer(string modelPath);
```

**Initialize 3D audio processor.**

Note: This interface is deprecated and does not need to be called.

## EnableSpatializer

```csharp
int EnableSpatializer(bool enable);
```

**Enable or disable 3D audio effects.**

Use this function to enable or disable 3D audio effects. When enabled, 3D audio effects are audible.

| Parameter | Description |
| --- | --- |
| enable | Enable 3D audio effects or not. |

## IsEnableSpatializer

**Get current 3D audio effect status.**

Use this function to query the current 3D audio effect status.

## GetMicListCount

**Get microphone device count \(desktop only\).**

## GetMicList

```csharp
int GetMicList(out List<TMGAudioDeviceInfo> ppDeviceInfoList, int nCount);
```

**List microphone devices \(desktop only\).**

Use this interface to enumerate microphone devices. Use together with [GetMicListCount](#getmiclistcount).

| Parameter | Description |
| --- | --- |
| nCount | Number of device info entries. |
| ppDeviceInfoList | Pointer to device info array. |

## SelectMic

```csharp
int SelectMic(string micId);
```

**Select microphone device \(desktop only\).**

Use this interface to select a microphone device. If not called or "0" is passed, the system default device is selected. The device ID of the first device returned by [GetMicList](#getmiclist) is the default device. If no device is selected, the default device is used for communication. After selection, the business layer maintains the communication device. If the selected device is unplugged, the communication device switches to the default device. When the unplugged device is reinserted, communication switches back to it.

| Parameter | Description |
| --- | --- |
| micId | Microphone device ID, from the device info list returned by GetMicList. |

## GetCurrentMic

```csharp
int GetCurrentMic(out TMGAudioDeviceInfo pDeviceInfo);
```

**Get current microphone device \(desktop only\).**

Use this interface to query the current microphone device.

| Parameter | Description |
| --- | --- |
| pDeviceInfo | Pointer to device info. |

## GetSpeakerListCount

**Get speaker device count \(desktop only\).**

## GetSpeakerList

```csharp
int GetSpeakerList(out List<TMGAudioDeviceInfo> ppDeviceInfoList, int nCount);
```

**List speaker devices \(desktop only\).**

Use this interface to enumerate speaker devices. Use together with [GetSpeakerListCount](#getspeakerlistcount).

| Parameter | Description |
| --- | --- |
| nCount | Number of device info entries. |
| ppDeviceInfoList | Pointer to device info array. |

## SelectSpeaker

```csharp
int SelectSpeaker(string pSpeakerID);
```

**Select speaker device \(desktop only\).**

Use this interface to select a playback device. If not called or "0" is passed, the system default playback device is selected.

| Parameter | Description |
| --- | --- |
| pSpeakerID | Speaker device ID, from the device info list returned by GetSpeakerList. |

## GetCurrentSpeaker

```csharp
int GetCurrentSpeaker(out TMGAudioDeviceInfo pDeviceInfo);
```

**Get current speaker device \(desktop only\).**

Use this interface to query the current speaker device.

| Parameter | Description |
| --- | --- |
| pDeviceInfo | Pointer to device info. |

## EnableCustomAudioCapture

```csharp
int EnableCustomAudioCapture(bool enable);
```

**Enable custom audio capture mode.**

When enabled, the SDK disables its internal audio capture process and no longer captures audio from the microphone. Only audio encoding and sending remain active.

You must continuously feed your own captured audio data to the SDK using [SendCustomAudioData](#sendcustomaudiodata).

| Parameter | Description |
| --- | --- |
| enable | Enable or not, default: `NO`. |

> **Note**
> 
> Echo cancellation \(AEC\) requires strict control of capture and playback timing. Enabling custom audio capture may cause AEC to become ineffective.

## SetAudioRoute

```csharp
int SetAudioRoute(ITMG_AUDIO_ROUTE route);
```

**Set audio route.**

Configure the audio route, specifying which device on the phone will play sound. Common playback devices are speaker and earpiece, so this interface is only applicable to mobile devices.

Phones typically have two playback devices: an earpiece at the top and a stereo speaker at the bottom.

When the audio route is set to earpiece, sound is quieter and only audible when close to the ear, providing privacy for calls.

When the audio route is set to speaker, sound is louder and can be heard without holding the phone to your ear, enabling hands-free mode.

| Parameter | Description |
| --- | --- |
| route | Audio route, i.e., output device \(speaker, earpiece\), default: `ITMG_AUDIO_ROUTE_SPEAKER`. |

## SendCustomAudioData

```csharp
int SendCustomAudioData(ref TMGAudioFrame frame);
```

**Send custom captured audio data to the SDK.**

Call this interface at precise intervals matching each frame's duration. Irregular intervals may cause audio stuttering.

The following field settings are recommended for TMGAudioFrame \(other fields are not required\):

- data: Audio frame buffer. Only PCM format is supported. Frame length supports \[5ms \~ 100ms\], recommended 20ms. Length calculation: \[48000 Hz, mono: 48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes\].
- sample\_rate: Sample rate, supports: 16000, 24000, 32000, 44100, 48000.
- channel: Channel count \(stereo data is interleaved\), mono: 1; stereo: 2.
- timestamp: Timestamp in milliseconds \(ms\). Use the timestamp recorded when the audio frame is captured \(after capturing a frame, you can call generateCustomPTS to get the timestamp\).
- bits\_type: Bit depth. Only supports 16bit--PCM\_BITS\_TYPE\_FIXED\_16.

| Parameter | Description |
| --- | --- |
| frame | Audio data. |

## EnableCustomAudioRendering

```csharp
int EnableCustomAudioRendering(bool enable);
```

**Enable custom audio playback.**

| Parameter | Description |
| --- | --- |
| enable | Enable custom audio playback or not; default is disabled. |

> **Note**
> 
> You must set this before entering the room for it to take effect. Setting after entering the room is not supported.
> 
> If you need to connect external audio devices or want to control audio playback logic yourself, enable custom audio playback with this interface.
> 
> > After enabling custom audio playback, the SDK will not use system audio interfaces for playback. You must retrieve audio frames to play from the SDK via [GetCustomAudioRenderingFrame](#getcustomaudiorenderingframe) and handle playback yourself.

## GetCustomAudioRenderingFrame

```csharp
int GetCustomAudioRenderingFrame(ref TMGAudioFrame frame);
```

**Retrieve playable audio data.**

Before calling this interface, enable custom audio playback via [EnableCustomAudioRendering](#enablecustomaudiorendering).

The following field settings are recommended for TMGAudioFrame \(other fields are not required\):

- sample\_rate: Sample rate, required. Supports 16000, 24000, 32000, 44100, 48000.
- channel: Channel count, required. Use 1 for mono, 2 for stereo \(stereo data is interleaved\).
- data: Buffer for retrieving audio data. Allocate memory based on frame length. PCM data supports 10ms or 20ms frame length, recommended 20ms.
- bits\_type: Bit depth. Only supports 16bit--PCM\_BITS\_TYPE\_FIXED\_16.

Calculation formula: sample rate × playback duration × channel count × 2 \(bytes per sample\). For example: 48000 Hz, mono, 20ms frame: 48000 × 0.02s × 1 × 16bit = 15360bit = 1920 bytes.

| Parameter | Description |
| --- | --- |
| frame | Audio frame. |

> **Note**
> 
> 1. Set sample\_rate and channel fields in frame in advance, and allocate the data buffer for the required frame length.
> 2. The SDK automatically fills the data buffer based on sample\_rate and channel.
> 3. It is recommended to call this function directly from the system's audio playback thread. After playing a frame, call this interface to get the next frame of audio data.

## TrackingVolume

```csharp
int TrackingVolume(float interval);
```

**Enable volume callback.**

| Parameter | Description |
| --- | --- |
| interval | Volume callback interval in seconds. |

> Note
> 
> User volume data is returned via the ITMG\_MAIN\_EVENT\_TYPE\_USER\_VOLUMES event.

## StopTrackingVolume

**Disable volume callback.**

## GetMicLevel

**Get real-time microphone volume.**

## GetSpeakerLevel

**Get real-time speaker volume.**

## GetSendStreamLevel

**Get real-time upstream audio volume.**

## GetRecvStreamLevel

```csharp
int GetRecvStreamLevel(String userID);
```

**Get real-time downstream audio volume for other users in the room.**

| Parameter | Description |
| --- | --- |
| userID | User ID of other users in the room. |

## StartMicDeviceTest

```csharp
int StartMicDeviceTest(int interval);
```

**Start microphone test \(desktop only\).**

| Parameter | Description |
| --- | --- |
| interval | Microphone volume callback interval. |

> Note
> 
> Test results are returned via the ITMG\_MAIN\_EVENT\_TYPE\_TEST\_MIC\_VOLUME event.

## StopMicDeviceTest

**Stop microphone test \(desktop only\).**

## StartSpeakerDeviceTest

```csharp
int StartSpeakerDeviceTest(string filePath);
```

**Start speaker test \(desktop only\).**

| Parameter | Description |
| --- | --- |
| filePath | Path to the audio file. |

> Note
> 
> Test results are returned via the ITMG\_MAIN\_EVENT\_TYPE\_TEST\_SPEAKER\_VOLUME event.

## StopSpeakerDeviceTest

**Stop speaker test \(desktop only\).**

## SetAudioFrameCallback

```csharp
void SetAudioFrameCallback(ITMGAudioFrameCallback callback);
```

**Set custom audio data callback.**

After setting this callback, the SDK returns audio data \(PCM format\) including:

- OnCapturedAudioFrame: Callback for locally captured microphone audio data.
- [OnLocalProcessedAudioFrame](#onlocalprocessedaudioframe): Callback for locally captured audio data after preprocessing.
- [OnPlayAudioFrame](#onplayaudioframe): Audio data for each remote user before mixing.
- [OnMixedPlayAudioFrame](#onmixedplayaudioframe): Callback for mixed audio data of all streams before system playback.
- [OnMixedAllAudioFrame](#onmixedallaudioframe): Callback for all audio data after mixing \(including captured and playback audio\).

> **Note**
> 
> Setting the callback to null stops the custom audio callback; setting it to a non-null value starts the custom audio callback.