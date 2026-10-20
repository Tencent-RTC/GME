# ITMGRoom

Copyright \(c\) 2025 Tencent. All rights reserved.

Module: TMGRoom@GMESDK

Function: Tencent Cloud GME room-related function interfaces.

## ITMGRoom

| Function List | Description |
| --- | --- |
| [GetRoomID](#getroomid) | Get the voice room ID. |
| [ChangeRoomType](#changeroomtype) | Change the local user's room audio type. |
| [GetRoomType](#getroomtype) | Get the current room audio type. |
| [StartRoomSharing](#startroomsharing) | Start cross-room voice interaction. |
| [StopRoomSharing](#stoproomsharing) | Stop cross-room voice interaction. |
| [SwitchRoom](#switchroom) | Switch rooms instantly. |
| [SendCustomData](#sendcustomdata) | Send custom messages. |
| [StopSendCustomData](#stopsendcustomdata) | Stop sending custom messages. |
| [UpdateAudioRecvRange](#updateaudiorecvrange) | Configure audio reception range. |
| [UpdateSpatializerRecvRange](#updatespatializerrecvrange) | Set 3D audio attenuation distance. |
| [UpdateSelfPosition](#updateselfposition) | Update player sound source orientation and coordinates in the room. |
| [UpdateOtherPosition](#updateotherposition) | Update spatial coordinates for a remote user. |
| [SendSEIMsg](#sendseimsg) | Send custom messages via the SEI channel. |
| [GetAITranscriberManager](#getaitranscribermanager) | Get an instance of the AI Transcriber Manager. |

## GetRoomID

**Get the voice room ID.**

## ChangeRoomType

```csharp
int ChangeRoomType(ITMGRoomType roomType);
```

**Change the local user's room audio type.**

This method changes the room audio type for the local user only.

| Parameter | Description |
| --- | --- |
| roomType | Room audio type. |

## GetRoomType

**Get the current room audio type.**

## StartRoomSharing

```csharp
int StartRoomSharing(string targetRoomID, string targetUserID);
```

**Start cross-room voice interaction.**

Call this method after successfully joining a room to initiate cross-room voice interaction. Once invoked, the local user can communicate with the specified target userID in the target room.

| Parameter | Description |
| --- | --- |
| targetRoomID | ID of the target room. |
| targetUserID | ID of the target user. |
| userSig | User authentication information. |

## StopRoomSharing

**Stop cross-room voice interaction.**

Call this method after joining a room to end cross-room voice interaction. After invocation, the local user will stop communicating with the target userID in the target room.

## SwitchRoom

```csharp
int SwitchRoom(string targetRoomID, string userSig);
```

**Switch rooms instantly.**

| Parameter | Description |
| --- | --- |
| targetRoomID | ID of the target room. |
| userSig | User authentication information. |

## SendCustomData

```csharp
int SendCustomData(byte[] data, int length, int repeatCount);
```

**Send custom messages.**

| Parameter | Description |
| --- | --- |
| data | Custom message data. |
| repeatCount | Number of retries. |

## StopSendCustomData

**Stop sending custom messages.**

## UpdateAudioRecvRange

```csharp
int UpdateAudioRecvRange(float range);
```

**Configure audio reception range.**

Set the audio reception range based on the game engine's distance metrics. This method can only be called after successfully joining a room.

You must use this method together with UpdateSelfPosition to update the sound source orientation.

Call this method once for it to take effect; you can modify the range as needed.

| Parameter | Description |
| --- | --- |
| range | Audio reception range. |

## UpdateSpatializerRecvRange

```csharp
int UpdateSpatializerRecvRange(float range);
```

**Set 3D audio attenuation distance.**

In 3D audio, the sound source volume decreases as the distance increases. When the distance exceeds the specified range, the volume drops to nearly zero.

| Parameter | Description |
| --- | --- |
| range | Attenuation distance for 3D audio. |

## UpdateSelfPosition

```csharp
int UpdateSelfPosition(float[] position, float[] axisForward, float[] axisRight, float[] axisUp);
```

**Update player sound source orientation and coordinates in the room.**

Update the player's sound source orientation and coordinates in the specified room. The server uses this information to determine voice reachability between players, enabling spatial audio effects. Call this method after successfully joining a room, and invoke it every frame \(for example, in Unity, call it in the Update method\).

If you want to enable 3D audio effects, set the axisForward, axisRight, and axisUp parameters according to the requirements for 3D audio.

| Parameter | Description |
| --- | --- |
| axisForward | Unit vector for the forward axis in the local coordinate system. |
| axisRight | Unit vector for the right axis in the local coordinate system. |
| axisUp | Unit vector for the up axis in the local coordinate system. |
| position | Coordinates in the world coordinate system \(order: forward, right, up\). |

## UpdateOtherPosition

```csharp
int UpdateOtherPosition(string userID, float[] position);
```

**Update spatial coordinates for a remote user.**

Set the spatial coordinates for a specified user in the room to enable 3D audio effects. By default, a user's spatial coordinates are automatically broadcast to other users in the room. You can also manually set spatial coordinates for remote users by calling this method.

| Parameter | Description |
| --- | --- |
| position | Spatial coordinates of the user. |
| userID | User ID to set spatial coordinates for. |

## SendSEIMsg

```csharp
int SendSEIMsg(string message, int repeatCount);
```

Send custom messages via the SEI channel.

The remote client receives messages via the ITMG\_MAIN\_EVENT\_TYPE\_RECV\_SEI\_MSG event. If repeatCount \> 1, the callback may receive multiple identical messages, so deduplication is required.

| Parameter | Description |
| --- | --- |
| message | Custom message, maximum length 1000 bytes. |
| repeatCount | Number of times to send the message, range \[1,3\]. If repeatCount \> 3, the send count is capped at 3. |

## GetAITranscriberManager

**Get an instance of the AI Transcriber Manager.**

Call this method to obtain an AI Transcriber Manager instance, which allows you to start and stop real-time transcription and manage transcription listeners.