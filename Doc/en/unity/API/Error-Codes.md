# 错误码表

Copyright \(c\) 2025 Tencent. All rights reserved.

Module: GME Error Code Table

Function: Notifies users of errors encountered during GME usage.

## Enum Types

| Enum Type | Description |
| --- | --- |
| QAVError | Error codes. |

## AVError

**Error codes**

| Enum | Value | Description |
| --- | --- | --- |
| OK | 0 | No error. |
| AV\_ERR\_UNKNOWN | 1 | Unknown error. |
| AV\_ERR\_FREQUENT\_OPERATION | 1000 | Operation frequency too high. The interface supports concurrent calls, but excessive operations may impact performance. Limit operation frequency. |
| AV\_ERR\_REPETITIVE\_OPERATION | 1001 | Duplicate operation. This error is returned if you attempt the same operation while it is already in progress. |
| AV\_ERR\_EXCLUSIVE\_OPERATION | 1002 | Exclusive operation. This error is returned if you attempt another operation of the same type while one is already in progress. |
| AV\_ERR\_HAS\_IN\_THE\_STATE | 1003 | Already in the target state. No further action needed. For example, if the device is already open and you try to open it again, this error is returned. |
| AV\_ERR\_INVALID\_ARGUMENT | 1004 | Invalid parameter. Verify the parameters passed to the API. |
| AV\_ERR\_TIMEOUT | 1005 | Server request timed out. |
| AV\_ERR\_NOT\_IMPLEMENTED | 1006 | API not implemented. |
| AV\_ERR\_REFUSED | 1007 | API call refused. |
| AV\_ERR\_INVALID\_LICENSE | 1008 | Invalid license. Call failed. |
| AV\_ERR\_DISCONNECTED | 1009 | Disconnected. |
| AV\_ERR\_CONTEXT\_NOT\_START | 1101 | GME SDK not initialized. Call the Init interface to initialize the GME SDK before proceeding. |
| AV\_ERR\_ROOM\_NOT\_EXIST | 1201 | Room does not exist. This operation must be called after successfully entering a room. |
| AV\_ERR\_ROOM\_NOT\_EXITED | 1202 | Room not exited. This operation must be called after leaving the voice room. |
| AV\_ERR\_DEVICE\_NOT\_EXIST | 1301 | Device not found. Verify that the audio device is valid. |
| AV\_ERR\_SERVER\_FAILED | 10001 | Server unable to process your request. |
| AV\_ERR\_VOICE\_RECORDER\_PARAM\_INVALID | 4097 | Recording parameter is missing. Verify that all parameters are correct. |
| AV\_ERR\_VOICE\_RECORDER\_NO\_MIC\_PERMISSION | 4098 | Microphone permission not granted. Ensure microphone access is enabled. |
| AV\_ERR\_VOICE\_RECORDER\_ALREADY\_STARTED | 4099 | Recording already started. Stop the current recording before starting a new one. |
| AV\_ERR\_VOICE\_RECORD\_AUDIO\_TOO\_SHORT | 4100 | No audio recorded. This may occur if collection is not enabled or the recording duration is too short. |
| AV\_ERR\_VOICE\_RECORDER\_OPENFILE\_ERROR | 4101 | Failed to open file. Verify the file path and check file read/write permissions. |
| AV\_ERR\_VOICE\_RECORD\_FORMAT\_NOT\_SUPPORTED | 4105 | Unsupported recording format. Refer to the official documentation for supported formats. |
| AV\_ERR\_VOICE\_RECORDER\_INNER\_ERROR | 4106 | Recording failed due to SDK internal error. Provide logs to developers for troubleshooting. |
| AV\_ERR\_VOICE\_PLAYER\_OPENFILE\_ERROR | 20484 | Failed to open file. Verify the file path and check file read/write permissions. |
| AV\_ERR\_VOICE\_PLAYER\_FORMAT\_NOT\_SUPPORTED | 20486 | Unsupported playback file format. Decoding failed. |
| AV\_ERR\_REQUEST\_IP\_TIMEOUT | 7001 | Failed to request media server list. Check network connectivity and ensure the firewall allows UDP traffic. |
| AV\_ERR\_CONNECT\_SERVER\_TIMEOUT | 7002 | Connection to media server timed out. |
| AV\_ERR\_ENTER\_ROOM\_FAILED | 7004 | Failed to enter voice room. |
| AV\_ERR\_AUTH\_FIALD | 7006 | UserSig authentication failed. Verify that the UserSig passed to the EnterRoom operation is valid. |
| AV\_ERR\_IN\_OTHER\_ROOM | 7007 | Room entry request refused. Check if you are calling EnterRoom repeatedly to enter rooms with the same ID. |
| AV\_ERR\_DISSOLVED\_OVERUSER | 7008 | Real-time voice service unavailable. Confirm that your package has remaining minutes and your Tencent Cloud account is not overdue. |
| AV\_ERR\_VOICE\_MESSAGE\_SERVICE\_INVALID | 7009 | Voice Message Service unavailable. Confirm that the service is enabled and your Tencent Cloud account is not overdue. |
| AV\_ERR\_SPEECH\_TO\_TEXT\_SERVICE\_INVALID | 7010 | Speech-to-Text service unavailable. Confirm that the service is enabled and your Tencent Cloud account is not overdue. |
| AV\_ERR\_TRANSLATE\_TEXT\_SERVICE\_INVALID | 7011 | Text Translation Service unavailable. Confirm that the service is enabled and your Tencent Cloud account is not overdue. |
| AV\_ERR\_TEXT\_TO\_SPEECH\_SERVICE\_INVALID | 7012 | Text-to-Speech Service unavailable. Confirm that the service is enabled and your Tencent Cloud account is not overdue. |
| AV\_ERR\_EFFECT\_OPENFILE\_FAILED | 4051 | Failed to open BGM audio file. Verify the file path. |
| AV\_ERR\_EFFECT\_DECODER\_FAILED | 4053 | BGM audio file decoding failed. Verify that the file format is supported. |
| AV\_ERR\_EFFECT\_STATE\_ILLIGAL | 4057 | Exceeded limit, such as preloading two background music tracks simultaneously. |
| AV\_ERR\_SYSTEM\_LOOPBACK\_START\_FAILED | 4058 | System loopback mixing failed to start. Possible causes: 1. System version unsupported. Specifying or excluding process mixing requires Windows 10.0.19042 \(20H2\) or later; specifying path mixing \(x64\) also requires Windows 10.0.19042 \(20H2\) or later. Check your system version. 2. Invalid parameters \(empty, nonexistent paths, invalid process IDs, invalid device names\). Verify all parameters. 3. No available speaker device. Confirm a speaker is available. |
| AV\_ERR\_SYSTEM\_LOOPBACK\_THIRD\_PARTY\_APP\_EXIT | 4059 | Third-party application loopback mixing error. This may occur if the specified process or application exits unexpectedly during sound collection. Check the process or application status and retry by re-entering the process ID. |
| AV\_ERR\_RECORD\_CREATEFILE\_FAILED | 5001 | Failed to create recording file. Verify the file path. |
| AV\_ERR\_RECORD\_FILE\_FORAMT\_NOTSUPPORT | 5002 | Unsupported recording file format. Verify all parameters. |
| AV\_ERR\_RECORD\_START\_FAILED | 5003 | Failed to start recording. |
| AV\_ERR\_OPERATOR\_DEVICE\_REFUSED | 6999 | Audio device operation prohibited. |
| AV\_ERR\_VOICE\_UPLOAD\_FILE\_ACCESSERROR | 8193 | File access error during upload. Verify the upload file path. |
| AV\_ERR\_VOICE\_UPLOAD\_SIGN\_CHECK\_FAIL | 8194 | UserSig authentication failed. Verify the UserSig parameter. |
| AV\_ERR\_VOICE\_UPLOAD\_COS\_INTERNAL\_FAIL | 8195 | Server error during file upload. Try again later. |
| AV\_ERR\_VOICE\_UPLOAD\_GET\_TOKEN\_NETWORK\_FAIL | 8196 | Network error while obtaining file upload token. Check network connectivity. |
| AV\_ERR\_VOICE\_UPLOAD\_SYSTEM\_INNER\_ERROR | 8197 | Server error while obtaining file upload token. Try again later. |
| AV\_ERR\_VOICE\_UPLOAD\_COS\_NETWORK\_FAIL | 8199 | Network error during file upload. Check network connectivity. |
| AV\_ERR\_VOICE\_DOWNLOAD\_FILE\_URL\_INVALID | 12288 | Invalid download URL. |
| AV\_ERR\_VOICE\_DOWNLOAD\_FILE\_ACCESS\_ERROR | 12289 | File access error during download. Verify the file save path. |
| AV\_ERR\_VOICE\_DOWNLOAD\_SIGN\_CHECK\_FAIL | 12290 | UserSig authentication failed during download. Verify the UserSig parameter. |
| AV\_ERR\_VOICE\_DOWNLOAD\_COS\_INTERNAL\_FAIL | 12291 | Server error during file download. Try again later. |
| AV\_ERR\_VOICE\_DOWNLOAD\_GET\_SIGN\_NETWORK\_FAIL | 12293 | Network error while obtaining file download token. Check network connectivity. |
| AV\_ERR\_VOICE\_DOWNLOAD\_SYSTEM\_INNER\_ERROR | 12294 | Server error while obtaining file download token. Try again later. |
| AV\_ERR\_VOICE\_DOWNLOAD\_COS\_NETWORK\_FAIL | 12298 | Network error during file download. Check network connectivity. |
| AV\_ERR\_VOICE\_DOWNLOAD\_OVER\_LIMIT | 12299 | Simultaneous file downloads exceed the limit. Maximum concurrent downloads allowed: 50. |
| AV\_ERR\_VOICE\_S2T\_SYSTEM\_INTERNAL\_ERROR | 32769 | System error caused Speech-to-Text failure. |
| AV\_ERR\_VOICE\_S2T\_NETWORK\_FAIL | 32770 | Network error prevented connection to Speech-to-Text service. |
| AV\_ERR\_VOICE\_S2T\_RSP\_DATA\_DECODE\_FAIL | 32772 | Network error caused Speech-to-Text failure. |
| AV\_ERR\_VOICE\_S2T\_SIGN\_CHECK\_FAIL | 32776 | Speech-to-Text authentication failed. |
| AV\_ERR\_VOICE\_S2T\_PARAM\_NULL | 32784 | Invalid Speech-to-Text parameters. |
| AV\_ERR\_VOICE\_S2T\_AUTO\_SPEECH\_REC\_ERROR | 32785 | Speech-to-Text cloud ASR error. |
| AV\_ERR\_VOICE\_STREAMIN\_RUNING\_ERROR | 32786 | Speech-to-Text operation already in progress. Duplicate request. |
| AV\_ERR\_VOICE\_FILE\_COS\_NOT\_FOUND | 32789 | File not found in Tencent Cloud COS. |
| AV\_ERR\_SHARE\_ROOM\_INVALID\_VALUE | 700004 | Invalid cross-room co-hosting parameters. |
| AV\_ERR\_SHARE\_ROOM\_TIMEOUT | 700008 | Cross-room co-hosting timed out. |
| AV\_ERR\_SHARE\_ROOM\_TYPE\_ERR | 700016 | Current role is Audience and cannot request or disconnect cross-room co-hosting. Switch to Host before proceeding. |
| GMESDK\_VERSION\_local | "local" | GME version. |