# 类型定义

Copyright \(c\) 2025 Tencent. All rights reserved.

Module: GME Key Type Definitions

Function: Definitions of commonly used structs, enums, and constants.

## Struct Types

| Function List | Description |
| --- | --- |
| [TMGAudioFrame](#tmgaudioframe) | Audio frame data. |
| [TMGAudioDeviceInfo](#tmgaudiodeviceinfo) | Audio device information. |
| [TMGNetworkQuality](#tmgnetworkquality) | Network quality statistics. |

## Enum Types

| Enum Type | Description |
| --- | --- |
| [ITMG\_LOG\_LEVEL](#itmg_log_level) | Log level. |
| [ITMG\_APP\_SCENE](#itmg_app_scene) | Application scenario. |
| [ITMG\_AUDIO\_MEMBER\_ROLE](#itmg_audio_member_role) | Role type. |
| [ITMGRoomType](#itmg_room_type) | Room type. |
| [ITMG\_MAIN\_EVENT\_TYPE](#itmg_main_event_type) | GME SDK event type. |
| [ITMG\_CUSTOMDATA\_SUB\_EVENT](#itmg_customdata_sub_event) | Custom data sub-events. |
| [ITMG\_RANGE\_AUDIO\_MODE](#itmg_range_audio_mode) | Range voice states. |
| [ITMG\_EVENT\_ID\_USER\_UPDATE](#itmg_event_id_user_update) | Member status change sub-events. |
| [ITMG\_PCM\_BITS\_TYPE](#itmg_pcm_bits_type) | PCM bit depth. |
| [ITMG\_NETWORK\_QUALITY](#itmg_network_quality) | Network quality. Use this value to display each user's network quality in the UI. |
| [ITMG\_MIC\_PERMISSION](#itmg_mic_permission) | Microphone permission type. |
| [ITMG\_AUDIO\_ROUTE](#itmg_audio_route) | Audio route \(playback mode\). |
| [ITMG\_ROOM\_MANAGEMENT\_OPERATOR](#itmg_room_management_operator) | Remote user audio device control sub-events. |
| [ITMG\_VOICE\_TYPE](#itmg_voice_type) | Voice changer effects. |

## ITMG\_LOG\_LEVEL

**Log level.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_LOG\_LEVEL\_NONE](#itmg_log_level) | -1 | Disable logs. |
| [ITMG\_LOG\_LEVEL\_ERROR](#itmg_log_level) | 1 | Output only error level logs. |
| [ITMG\_LOG\_LEVEL\_INFO](#itmg_log_level) | 2 | Output info and error level logs. |
| [ITMG\_LOG\_LEVEL\_DEBUG](#itmg_log_level) | 3 | Output debug, info, and error level logs. |
| [ITMG\_LOG\_LEVEL\_VERBOSE](#itmg_log_level) | 4 | Output verbose, debug, info, and error level logs. |

## ITMG\_APP\_SCENE

**Application scenario.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_APP\_SCENE\_RTC](#itmg_app_scene) | 2 | Real-time voice chat. Supports up to 300 users per room, with up to 50 users speaking at the same time. All users are hosts by default and can speak freely. |
| [ITMG\_APP\_SCENE\_LIVE](#itmg_app_scene) | 3 | Audio live streaming and game voice. Supports up to 100,000 audience members in a single room. Users are audience by default and cannot speak; to become a host, call SetAudioRole before or after joining the room. |

## ITMG\_AUDIO\_MEMBER\_ROLE

**Role type.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_AUDIO\_MEMBER\_ROLE\_ANCHOR](#itmg_audio_member_role) | 0 | Host role. Can publish their own audio stream at any time. |
| [ITMG\_AUDIO\_MEMBER\_ROLE\_AUDIENCE](#itmg_audio_member_role) | 1 | Audience role. Can only listen to the host's audio stream and cannot publish their own audio stream. To publish, call SetAudioRole before or after joining the room to switch to host. |

## ITMG\_ROOM\_TYPE

**Room type.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_ROOM\_TYPE\_FLUENCY](#itmg_room_type) | 1 | Fluent audio quality, mono, 18kbps bitrate. Optimized for fluency and ultra-low latency real-time voice. Ideal for in-game voice chat \(FPS, MOBA, etc.\). |
| [ITMG\_ROOM\_TYPE\_STANDARD](#itmg_room_type) | 2 | Standard audio quality, mono, 50kbps bitrate. Good audio quality, moderate latency. Suitable for casual games \(Werewolf, card games, etc.\). |
| [ITMG\_ROOM\_TYPE\_HIGHQUALITY](#itmg_room_type) | 3 | High-definition audio quality, full-band stereo, 128kbps bitrate. Ultra-high audio quality with higher latency. Recommended for music/dance games, voice interaction apps, and scenarios requiring high audio quality \(music playback, online karaoke\). |

## ITMG\_MAIN\_EVENT\_TYPE

**GME SDK event type.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_MAIN\_EVENT\_TYPE\_ENTER\_ROOM](#itmg_main_event_type) | 1 | Enter real-time voice room event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_EXIT\_ROOM](#itmg_main_event_type) | 2 | Exit real-time voice room event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_ROOM\_DISCONNECT](#itmg_main_event_type) | 3 | Room disconnected due to network or other reasons. |
| [ITMG\_MAIN\_EVENT\_TYPE\_USER\_UPDATE](#itmg_main_event_type) | 4 | Member status change event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_NUMBER\_OF\_USERS\_UPDATE](#itmg_main_event_type) | 7 | Deprecated. |
| [ITMG\_MAIN\_EVENT\_TYPE\_NUMBER\_OF\_AUDIOSTREAMS\_UPDATE](#itmg_main_event_type) | 8 | Deprecated. |
| [ITMG\_MAIN\_EVENT\_TYPE\_RECONNECT\_START](#itmg_main_event_type) | 11 | Room reconnection started. |
| [ITMG\_MAIN\_EVENT\_TYPE\_RECONNECT\_SUCCESS](#itmg_main_event_type) | 12 | Room reconnection succeeded. |
| [ITMG\_MAIN\_EVENT\_TYPE\_SWITCH\_ROOM](#itmg_main_event_type) | 13 | Quick room switch result event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_ROOM\_SHARING\_START](#itmg_main_event_type) | 23 | Cross-room communication request result event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_ROOM\_SHARING\_STOP](#itmg_main_event_type) | 24 | End cross-room communication callback. |
| [ITMG\_MAIN\_EVENT\_TYPE\_RECORD\_COMPLETED](#itmg_main_event_type) | 30 | Audio recording completed event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_SPEAKER\_DEFAULT\_DEVICE\_CHANGED](#itmg_main_event_type) | 1008 | Default speaker device changed \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_SPEAKER\_NEW\_DEVICE](#itmg_main_event_type) | 1009 | New speaker device added \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_SPEAKER\_LOST\_DEVICE](#itmg_main_event_type) | 1010 | Speaker device removed \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MIC\_NEW\_DEVICE](#itmg_main_event_type) | 1011 | New microphone device added \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MIC\_LOST\_DEVICE](#itmg_main_event_type) | 1012 | Microphone device removed \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MIC\_DEFAULT\_DEVICE\_CHANGED](#itmg_main_event_type) | 1013 | Default microphone device changed \[Windows only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_SYSTEM\_LOOPBACK\_START\_FAILED](#itmg_main_event_type) | 1014 | System loopback start failed \[Windows/Mac only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_USER\_VOLUMES](#itmg_main_event_type) | 1020 | User volume change event in the room. |
| [ITMG\_MAIN\_EVENT\_TYPE\_NETWORK\_QUALITY](#itmg_main_event_type) | 1021 | Network call quality event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_CHANGE\_ROOM\_QUALITY](#itmg_main_event_type) | 1022 | Room call quality monitoring event \(deprecated, use ITMG\_MAIN\_EVENT\_TYPE\_NETWORK\_QUALITY\). |
| [ITMG\_MAIN\_EVENT\_TYPE\_USER\_SPECTRUMS](#itmg_main_event_type) | 1023 | User spectrum data in the room. |
| [ITMG\_MAIN\_EVENT\_TYPE\_USER\_VAD](#itmg_main_event_type) | 1024 | User VAD status callback event in the room. |
| [ITMG\_MAIN\_EVENT\_TYPE\_TEST\_MIC\_VOLUME](#itmg_main_event_type) | 1030 | Microphone test callback \[desktop only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_TEST\_SPEAKER\_VOLUME](#itmg_main_event_type) | 1031 | Speaker test callback \[desktop only\]. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MUSIC\_PLAY\_START](#itmg_main_event_type) | 1087 | BGM playback started. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MUSIC\_PLAY\_PROGRESS](#itmg_main_event_type) | 1088 | BGM playback progress event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MUSIC\_PLAY\_PAUSE](#itmg_main_event_type) | 1089 | BGM playback paused. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MUSIC\_PLAY\_RESUME](#itmg_main_event_type) | 1090 | BGM playback resumed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_MUSIC\_PLAY\_FINISH](#itmg_main_event_type) | 1091 | BGM playback completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_CUSTOMDATA\_UPDATE](#itmg_main_event_type) | 1092 | Custom data event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_RECV\_SEI\_MSG](#itmg_main_event_type) | 1093 | SEI custom data event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_RECORD\_FIRST\_FRAME](#itmg_main_event_type) | 5000 | Voice message recording, first audio frame event. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_RECORD\_COMPLETE](#itmg_main_event_type) | 5001 | Voice message recording completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_UPLOAD\_COMPLETE](#itmg_main_event_type) | 5002 | Voice message file upload completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_DOWNLOAD\_COMPLETE](#itmg_main_event_type) | 5003 | Voice message file download completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_PLAY\_COMPLETE](#itmg_main_event_type) | 5004 | Voice message playback completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_SPEECH2TEXT\_COMPLETE](#itmg_main_event_type) | 5005 | Voice message speech-to-text completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_STREAMINGRECOGNITION\_COMPLETE](#itmg_main_event_type) | 5006 | Streaming speech-to-text completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_STREAMINGRECOGNITION\_IS\_RUNNING](#itmg_main_event_type) | 5007 | Streaming speech-to-text in progress. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_TEXT2SPEECH\_COMPLETE](#itmg_main_event_type) | 5008 | Text-to-speech completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_PTT\_TRANSLATE\_TEXT\_COMPLETE](#itmg_main_event_type) | 5009 | Text translation completed. |
| [ITMG\_MAIN\_EVENT\_TYPE\_ROOM\_MANAGEMENT\_OPERATOR](#itmg_main_event_type) | 6000 | Remote user audio device control event. |

## ITMG\_CUSTOMDATA\_SUB\_EVENT

**Custom data sub-events.**

| Enum | Value | Description |
| --- | --- | --- |
| ITMG\_CUSTOMDATA\_AV\_SUB\_EVENT\_UPDATE | 0 | Custom data event. |
| ITMG\_CUSTOMDATA\_AV\_SUB\_EVENT\_AI\_CONVERSATION | 1 | AI conversation message event. |

## ITMG\_RANGE\_AUDIO\_MODE

**Range voice states.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_ALL\_REC\_ALL](#itmg_range_audio_mode) | 1 | Default mode: send audio to all players in the room and receive audio from all players. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_ALL\_REC\_BOTH](#itmg_range_audio_mode) | 2 | Host mode: send audio to all players and receive audio from nearby and team players. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_TEAM\_REC\_TEAM](#itmg_range_audio_mode) | 3 | Team mode: send audio only to team players and receive only team players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_TEAM\_REC\_PROX](#itmg_range_audio_mode) | 4 | Send audio only to team players and receive only nearby players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_TEAM\_REC\_BOTH](#itmg_range_audio_mode) | 5 | Send audio only to team players and receive audio from both nearby and team players. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_PROX\_REC\_TEAM](#itmg_range_audio_mode) | 6 | Send audio only to nearby players and receive only team players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_PROX\_REC\_PROX](#itmg_range_audio_mode) | 7 | Range mode: send audio only to nearby players and receive only nearby players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_PROX\_REC\_BOTH](#itmg_range_audio_mode) | 8 | Send audio only to nearby players and receive audio from both nearby and team players. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_BOTH\_REC\_TEAM](#itmg_range_audio_mode) | 9 | Send audio to both nearby and team players, receive only team players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_BOTH\_REC\_PROX](#itmg_range_audio_mode) | 10 | Send audio to both nearby and team players, receive only nearby players' audio. |
| [ITMG\_RANGE\_AUDIO\_MODE\_SND\_BOTH\_REC\_BOTH](#itmg_range_audio_mode) | 11 | Range + team mode: send audio to both nearby and team players, receive audio from both nearby and team players. |

## ITMG\_EVENT\_ID\_USER\_UPDATE

**Member status change sub-events.**

| Enum | Value | Description |
| --- | --- | --- |
| ITMG\_EVENT\_ID\_USER\_ENTER | 1 | User entered voice room. |
| ITMG\_EVENT\_ID\_USER\_EXIT | 2 | User exited voice room. |
| ITMG\_EVENT\_ID\_USER\_MIC\_OPENED | 3 | User enabled microphone. |
| ITMG\_EVENT\_ID\_USER\_MIC\_CLOSED | 4 | User disabled microphone. |
| ITMG\_EVENT\_ID\_USER\_HAS\_AUDIO | 5 | User sent audio data. Returns the UserID of the speaking user. Use this event to detect if a user is speaking and display voiceprint effects. |
| ITMG\_EVENT\_ID\_USER\_NO\_AUDIO | 6 | User stopped sending audio data. Returns the UserID of the user who stopped speaking. |

## ITMG\_PCM\_BITS\_TYPE

**PCM bit depth.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_PCM\_BITS\_TYPE\_FIXED\_16](#itmg_pcm_bits_type) | 0 | 16-bit |
| [ITMG\_PCM\_BITS\_TYPE\_FLOAT\_32](#itmg_pcm_bits_type) | 1 | 32-bit |

## ITMG\_NETWORK\_QUALITY

**Network quality. Use this value to display each user's network quality in the UI.**

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_NETWORK\_QUALITY\_UNKNOWN](#itmg_network_quality) | 0 | Undefined. |
| [ITMG\_NETWORK\_QUALITY\_EXCELLENT](#itmg_network_quality) | 1 | Network is excellent. |
| [ITMG\_NETWORK\_QUALITY\_GOOD](#itmg_network_quality) | 2 | Network is good. |
| [ITMG\_NETWORK\_QUALITY\_POOR](#itmg_network_quality) | 3 | Network is average. |
| [ITMG\_NETWORK\_QUALITY\_BAD](#itmg_network_quality) | 4 | Network is poor. |
| [ITMG\_NETWORK\_QUALITY\_VBAD](#itmg_network_quality) | 5 | Network is very poor. |
| [ITMG\_NETWORK\_QUALITY\_DOWN](#itmg_network_quality) | 6 | Network does not meet the minimum requirements for GME SDK. |

## ITMG\_MIC\_PERMISSION

**Microphone permission type.**

| Enum | Value | Description |
| --- | --- | --- |
| ITMG\_PERMISSION\_GRANTED | 0 | Microphone authorized. |
| ITMG\_PERMISSION\_Denied | 1 | Microphone denied. |
| ITMG\_PERMISSION\_NotDetermined | 2 | Permission unknown, needs to request permission. |

## ITMG\_AUDIO\_ROUTE

**Audio route \(playback mode\)**

Audio route determines whether sound is played through the phone's speaker or earpiece. This interface is only available on mobile devices.

A mobile phone has two speakers: the earpiece at the top and the stereo speaker at the bottom.

- When the audio route is set to earpiece, sound is quieter and only audible when close to the ear, providing greater privacy. Recommended for phone calls.
- When the audio route is set to speaker, sound is louder and can be heard without holding the phone to your ear, enabling hands-free use.

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_AUDIO\_ROUTE\_UNKNOWN](#itmg_audio_route) | -1 | Unknown: unknown route device. |
| [ITMG\_AUDIO\_ROUTE\_SPEAKER](#itmg_audio_route) | 0 | Speakerphone: plays through speaker \(hands-free\), speaker is at the bottom of the phone, louder sound, suitable for music playback. |
| [ITMG\_AUDIO\_ROUTE\_EARPIECE](#itmg_audio_route) | 1 | Earpiece: plays through earpiece, earpiece is at the top of the phone, quieter sound, suitable for privacy-sensitive call scenarios. |

## ITMG\_ROOM\_MANAGEMENT\_OPERATOR

**Remote user audio device control sub-events.**

| Enum | Value | Description |
| --- | --- | --- |
| ITMG\_ROOM\_MANAGEMENT\_MIC\_OP | 0 | Microphone control event. |
| ITMG\_ROOM\_MANAGERMENT\_FORBID\_OP | 1 | Forbid microphone and speaker operation event. |

## ITMG\_VOICE\_TYPE

**Voice changer effects.**

Voice changer effects modify the human voice using acoustic algorithms to produce a timbre different from the original.

| Enum | Value | Description |
| --- | --- | --- |
| [ITMG\_VOICE\_TYPE\_ORIGINAL\_SOUND](#itmg_voice_type) | 0 | Disable effects. |
| [ITMG\_VOICE\_TYPE\_KINDER\_GARTEN](#itmg_voice_type) | 1 | Kindergarten. |
| [ITMG\_VOICE\_TYPE\_LOLITA](#itmg_voice_type) | 2 | Lolita. |
| [ITMG\_VOICE\_TYPE\_UNCLE](#itmg_voice_type) | 3 | Uncle. |
| [ITMG\_VOICE\_TYPE\_HEAVY\_MENTAL](#itmg_voice_type) | 4 | Heavy metal. |
| [ITMG\_VOICE\_TYPE\_INFLUENZA](#itmg_voice_type) | 5 | Flu. |
| [ITMG\_VOICE\_TYPE\_DIALECT](#itmg_voice_type) | 6 | Foreigner. |
| [ITMG\_VOICE\_TYPE\_CAGED\_ANIMAL](#itmg_voice_type) | 7 | Caged animal. |
| [ITMG\_VOICE\_TYPE\_DEAD\_FATBOY](#itmg_voice_type) | 8 | Dead fatboy. |
| [ITMG\_VOICE\_TYPE\_STRONG\_CURRENT](#itmg_voice_type) | 9 | Strong current. |
| [ITMG\_VOICE\_TYPE\_HEAVY\_MACHINE](#itmg_voice_type) | 10 | Heavy machine. |
| [ITMG\_VOICE\_TYPE\_INTANGIBLE](#itmg_voice_type) | 11 | Ethereal. |
| [ITMG\_VOICE\_TYPE\_PIGSY](#itmg_voice_type) | 12 | Pigsy. |
| [ITMG\_VOICE\_TYPE\_HULK](#itmg_voice_type) | 13 | Hulk. |

## TMGAudioFrame

**Audio frame data.**

| Enum Type | Description |
| --- | --- |
| bits\_type | Bit depth. |
| channel | Number of channels. |
| data | Audio data. |
| length | Audio data length. |
| sample\_rate | Sample rate. |
| timestamp | Timestamp \(ms\). |

## TMGAudioDeviceInfo

**Audio device information.**

This struct is used in the GetMicList and GetSpeakerList APIs.

| Enum Type | Description |
| --- | --- |
| m\_strDeviceID | Device ID. |
| m\_strDeviceName | Device name. |

## TMGNetworkQuality

**Network quality statistics.**

This struct is used in the QAVNetworkQualityStatistics delegate.

| Enum Type | Description |
| --- | --- |
| downLoss | Downlink packet loss rate from cloud to SDK \(%\). |
| quality | Network quality. |
| rtt | Round-trip latency from SDK to cloud \(ms\). |
| upLoss | Uplink packet loss rate from SDK to cloud \(%\). |
| userID | User ID. Empty means self. |