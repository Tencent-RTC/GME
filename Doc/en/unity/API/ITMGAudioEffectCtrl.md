# ITMGAudioEffectCtrl

Copyright \(c\) 2025 Tencent. All rights reserved.

Module: TMGAudioEffectCtrl@GMESDK

Function: Tencent Cloud GME Audio Effect API

## ITMGAudioEffectCtrl

| Function List | Description |
| --- | --- |
| [StartPlayMusic](#startplaymusic) | Play background music. |
| [StopPlayMusic](#stopplaymusic) | Stop background music. |
| [PausePlayMusic](#pauseplaymusic) | Pause background music. |
| [ResumePlayMusic](#resumeplaymusic) | Resume background music. |
| [IsMusicPlayEnd](#ismusicplayend) | Check if background music playback has finished. |
| [SetAllMusicVolume](#setallmusicvolume) | Adjust local and remote volume for all background music tracks. |
| [SetMusicPublishVolume](#setmusicpublishvolume) | Set remote volume for a specific background music track. |
| [GetMusicPublishVolume](#getmusicpublishvolume) | Retrieve remote volume for a specific background music track. |
| [SetMusicPlayoutVolume](#setmusicplayoutvolume) | Set local volume for a specific background music track. |
| [GetMusicPlayoutVolume](#getmusicplayoutvolume) | Retrieve local volume for a specific background music track. |
| [SetMusicPitch](#setmusicpitch) | Adjust background music pitch. |
| [GetMusicDurationInMS](#getmusicdurationinms) | Get background music duration \(milliseconds\). |
| [GetMusicCurrentPosInMS](#getmusiccurrentposinms) | Get playback position of background music \(milliseconds\). |
| [SeekMusicToPosInTime](#seekmusictoposintime) | Set playback position of background music \(milliseconds\). |
| [EnableMusicPublish](#enablemusicpublish) | Publish background music \(by sound\_id\) to remote users. |
| [EnableMusicPlayout](#enablemusicplayout) | Play background music \(by sound\_id\) locally. |
| [SetVoiceType](#setvoicetype) | Apply voice-changing effects. |
| [SetKaraokeType](#setkaraoketype) | Apply vocal reverb effects. |
| [StartRecord](#startrecord) | Start audio recording. |
| [StopRecord](#stoprecord) | Stop audio recording. |
| [StartSystemAudioLoopback](#startsystemaudioloopback) | Start system audio capture. |
| [StopSystemAudioLoopback](#stopsystemaudioloopback) | Stop system audio capture. |
| [SetSystemAudioLoopbackVolume](#setsystemaudioloopbackvolume) | Set system audio capture volume. |

## Enum Types

| Enum Type | Description |
| --- | --- |
| [ITMG\_AUDIO\_RECORDING\_CONTENT](#itmg_audio_recording_content) | Audio recording content type. |
| [ITMG\_KARAOKE\_TYPE](#itmg_karaoke_type) | Vocal reverb effects. |

## StartPlayMusic

```csharp
int StartPlayMusic(int soundId, string filePath, int loopCount);
```

**Play background music.**

Each music track must be assigned an ID, which is used to start or stop playback and adjust its volume.

| Parameter | Description |
| --- | --- |
| filePath | Path to the music file. |
| loopCount | Number of times to play. Use -1 for infinite loop, or specify 1-N for exact repetitions. |
| soundId | Music ID \(integer greater than 0\). |

> **Note**
> 
> 1. To play the same background music multiple times, use the same ID for each playback. Do not assign a new ID.
> 2. To play multiple tracks simultaneously, assign a unique ID to each track.
> 3. If you use the same ID for different tracks, the SDK will stop the previous track before starting the new one.

## StopPlayMusic

```csharp
int StopPlayMusic(int soundId);
```

**Stop background music.**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## PausePlayMusic

```csharp
int PausePlayMusic(int soundId);
```

**Pause background music.**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## ResumePlayMusic

```csharp
int ResumePlayMusic(int soundId);
```

**Resume background music.**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## IsMusicPlayEnd

```csharp
int IsMusicPlayEnd(int soundId);
```

**Check if background music playback has finished.**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## SetAllMusicVolume

```csharp
int SetAllMusicVolume(int volume);
```

**Adjust local and remote volume for all background music tracks.**

Use this API to set both local and remote volume levels for all background music tracks.

- Local volume: Volume heard by the host.
- Remote volume: Volume heard by the audience.

| Parameter | Description |
| --- | --- |
| volume | Volume level \(range: 0–200, default: 100\). |

> **Note**
> 
> If the volume is too low at 100, you can increase it up to 200. Setting volume above 100 may cause distortion. Adjust with caution.

## SetMusicPublishVolume

```csharp
int SetMusicPublishVolume(int soundId, int volume);
```

**Set remote volume for a specific background music track.**

Use this API for granular control of remote volume for each background music track \(audience side\).

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |
| volume | Volume level \(range: 0–200, default: 100\). |

> **Note**
> 
> If the volume is too low at 100, you can increase it up to 200. Setting volume above 100 may cause distortion. Adjust with caution.

## GetMusicPublishVolume

```csharp
int GetMusicPublishVolume(int soundId);
```

**Retrieve remote volume for a specific background music track.**

Use this API to get the remote volume for each background music track \(audience side\).

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## SetMusicPlayoutVolume

```csharp
int SetMusicPlayoutVolume(int soundId, int volume);
```

**Set local volume for a specific background music track.**

Use this API for granular control of local volume for each background music track \(host side\).

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |
| volume | Volume level \(range: 0–200, default: 100\). |

> **Note**
> 
> If the volume is too low at 100, you can increase it up to 200. Setting volume above 100 may cause distortion. Adjust with caution.

## GetMusicPlayoutVolume

```csharp
int GetMusicPlayoutVolume(int soundId);
```

**Retrieve local volume for a specific background music track.**

Use this API to get the local volume for each background music track \(host side\).

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## SetMusicPitch

```csharp
int SetMusicPitch(int soundId, float pitch);
```

**Adjust background music pitch.**

| Parameter | Description |
| --- | --- |
| pitch | Pitch \(default: 0.0f, range: -1.0 to 1.0\). |
| soundId | Music ID. |

## GetMusicDurationInMS

```csharp
int GetMusicDurationInMS(int soundId);
```

**Get background music duration \(milliseconds\).**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## GetMusicCurrentPosInMS

```csharp
int GetMusicCurrentPosInMS(int soundId);
```

**Get playback position of background music \(milliseconds\).**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |

## SeekMusicToPosInTime

```csharp
int SeekMusicToPosInTime(int soundId, int time);
```

**Set playback position of background music \(milliseconds\).**

| Parameter | Description |
| --- | --- |
| soundId | Music ID. |
| time | Playback position \(milliseconds\). |

## EnableMusicPublish

```csharp
int EnableMusicPublish(int soundId, bool enable);
```

**Publish background music \(by sound\_id\) to remote users.**

| Parameter | Description |
| --- | --- |
| enable | Enable publishing. |
| soundId | Music ID. |

## EnableMusicPlayout

```csharp
int EnableMusicPlayout(int soundId, bool enable);
```

**Play background music \(by sound\_id\) locally.**

| Parameter | Description |
| --- | --- |
| enable | Enable playback. |
| soundId | Music ID. |

## SetVoiceType

```csharp
int SetVoiceType(ITMG_VOICE_TYPE voiceType);
```

Apply voice-changing effects.

Use this API to apply voice-changing effects. For available effects, see [`ITMG_VOICE_TYPE`](Type-Definitions.md#itmg_voice_type) in [Type Definitions](Type-Definitions.md#itmg_voice_type).

| Parameter | Description |
| --- | --- |
| type | Voice effect type. |

> **Note**
> 
> The effect will expire automatically after leaving the room. To reapply the effect after rejoining, call this API again.

## SetKaraokeType

```csharp
int SetKaraokeType(ITMG_KARAOKE_TYPE type);
```

**Apply vocal reverb effects.**

Use this API to apply vocal reverb effects. For available effects, see ITMG\_KARAOKE\_TYPE in [Audio Effect API Reference](#itmg_karaoke_type).

| Parameter | Description |
| --- | --- |
| type | Reverb effect type. |

> **Note**
> 
> The effect will expire automatically after leaving the room. To reapply the effect after rejoining, call this API again.

## StartRecord

```csharp
int StartRecord(string filePath, ITMG_AUDIO_RECORDING_CONTENT content);
```

**Start audio recording.**

Use this API to record audio from the real-time voice room to a file. For supported audio data types, see ITMG\_AUDIO\_RECORDING\_CONTENT.

| Parameter | Description |
| --- | --- |
| content | Audio recording content type. |
| filePath | Path to the audio file. |

## StopRecord

**Stop audio recording.**

## StartSystemAudioLoopback

```csharp
int StartSystemAudioLoopback(string playerPath);
```

**Start system audio capture.**

This API captures audio from the computer's sound card and mixes it into the SDK's audio stream, allowing other users in the room to hear audio played by the host's computer.

| Parameter | Description |
| --- | --- |
| playerPath | Set to null \(nullptr\) to capture all system audio. |

> **Note**
> 
> - On Windows, set `playerPath` to the absolute path of an application's executable \(e.g., QQMusic.exe\) to capture audio from that application only \(supported in 32-bit SDK; 64-bit SDK requires Windows 10.0.19042 or higher\).
> - You can specify a speaker device name to capture audio from a specific speaker \(use TXDeviceManager's getDevicesList API for TXMediaDeviceTypeSpeaker\).
> - On Windows, specify the parameter as a process ID \("process\_xxx", where xxx is the process ID\) to capture audio from that process \(requires Windows 10.0.19042 or higher\).
> - On Windows, specify the parameter as "exclude\_process\_xxx" to capture all audio except that process \(requires Windows 10.0.19042 or higher\).

## StopSystemAudioLoopback

**Stop system audio capture.**

## SetSystemAudioLoopbackVolume

```csharp
int SetSystemAudioLoopbackVolume(int volume);
```

**Set system audio capture volume.**

| Parameter | Description |
| --- | --- |
| volume | Volume level \(range: 0–200, default: 100\). |

## ITMG\_AUDIO\_RECORDING\_CONTENT

**Audio recording content type.**

When calling StartRecord, select the type of audio content to record.

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_AUDIO\_RECORDING\_CONTENT\_ALL](#itmg_audio_recording_content) | 0 | Record both local and remote audio. |
| [ITMG\_AUDIO\_RECORDING\_CONTENT\_LOCAL](#itmg_audio_recording_content) | 1 | Record only local audio. |
| [ITMG\_AUDIO\_RECORDING\_CONTENT\_REMOTE](#itmg_audio_recording_content) | 2 | Record only remote audio. |

## ITMG\_KARAOKE\_TYPE

**Vocal reverb effects.**

Apply reverb effects to vocals using acoustic algorithms to simulate various immersive environments.

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_KARAOKE\_TYPE\_0](#itmg_karaoke_type) | 0 | Disable effect. |
| [ITMG\_KARAOKE\_TYPE\_1](#itmg_karaoke_type) | 1 | KTV |
| [ITMG\_KARAOKE\_TYPE\_2](#itmg_karaoke_type) | 2 | Small room |
| [ITMG\_KARAOKE\_TYPE\_3](#itmg_karaoke_type) | 3 | Auditorium |
| [ITMG\_KARAOKE\_TYPE\_4](#itmg_karaoke_type) | 4 | Deep |
| [ITMG\_KARAOKE\_TYPE\_5](#itmg_karaoke_type) | 5 | Loud |
| [ITMG\_KARAOKE\_TYPE\_6](#itmg_karaoke_type) | 6 | Metallic |
| [ITMG\_KARAOKE\_TYPE\_7](#itmg_karaoke_type) | 7 | Magnetic |
| [ITMG\_KARAOKE\_TYPE\_8](#itmg_karaoke_type) | 8 | Ethereal |
| [ITMG\_KARAOKE\_TYPE\_9](#itmg_karaoke_type) | 9 | Studio |
| [ITMG\_KARAOKE\_TYPE\_10](#itmg_karaoke_type) | 10 | Melodious |
| [ITMG\_KARAOKE\_TYPE\_11](#itmg_karaoke_type) | 11 | Studio 2 |