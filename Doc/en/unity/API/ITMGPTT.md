# ITMGPTT

Copyright \(c\) 2025 Tencent. All rights reserved.

Module:   TMGPTT@GMESDK

Function: Tencent Cloud GME Offline Voice Feature APIs

## ITMGPTT

| Function List | Description |
| --- | --- |
| [ApplyPTTAuthbuffer](#applypttauthbuffer) | Apply authentication credentials. |
| [SetMaxMessageLength](#setmaxmessagelength) | Set maximum voice message duration. |
| [StartRecording](#startrecording) | Start recording. |
| [StopRecording](#stoprecording) | Stop recording. |
| [CancelRecording](#cancelrecording) | Cancel recording. |
| [UploadRecordedFile](#uploadrecordedfile) | Upload voice file. |
| [DownloadRecordedFile](#downloadrecordedfile) | Download voice file. |
| [PlayRecordedFile](#playrecordedfile) | Play voice file. |
| [PlayRecordedFile](#playrecordedfile-1) | Play voice file. |
| [StopPlayFile](#stopplayfile) | Stop playing voice file. |
| [SpeechToText](#speechtotext) | Convert voice file to text. |
| [SpeechToText](#speechtotext-1) | Convert voice file to text \(with language selection\). |
| [SpeechToText](#speechtotext-2) | Convert voice file to text \(with language selection\). |
| [TranslateText](#translatetext) | Translate text. |
| [GetFileSize](#getfilesize) | Get voice file size. |
| [GetVoiceFileDuration](#getvoicefileduration) | Get voice file duration. |
| [StartRecordingWithStreamingRecognition](#startrecordingwithstreamingrecognition) | Start streaming voice recognition. |
| [StartRecordingWithStreamingRecognition](#startrecordingwithstreamingrecognition-1) | Start streaming voice recognition. |
| [StartRecordingWithStreamingRecognition](#startrecordingwithstreamingrecognition-2) | Start streaming voice recognition. |
| [SetPTTSourceLanguage](#setpttsourcelanguage) | Set PTT source language. |
| [TextToSpeech](#texttospeech) | Convert text to speech. |

## ApplyPTTAuthbuffer

```csharp
int ApplyPTTAuthbuffer(string userSig);
```

Apply authentication credentials.

After generating authentication credentials, assign them to the SDK.

| Parameter | Description |
| --- | --- |
| userSig | Authentication credentials. |

## SetMaxMessageLength

```csharp
int SetMaxMessageLength(int msTime);
```

**Set maximum voice message duration.**

Configure the maximum duration for voice message recording.

| Parameter | Description |
| --- | --- |
| msTime | Voice duration in milliseconds. Range: \[-1, 1000-180000\]. If set to -1, `StartRecordingWithStreamingRecognition` enables long-duration voice recognition, but the server will not store the recording file. |

## StartRecording

```csharp
int StartRecording(string filePath);
```

**Start recording.**

Begin recording a voice message.

| Parameter | Description |
| --- | --- |
| filePath | Path to save the voice file. The file extension must be `.ogg`. |

## StopRecording

**Stop recording.**

Stop the current recording session. This API is asynchronous; a callback is triggered when recording is complete. The voice file is available only after the callback returns successfully.

## CancelRecording

**Cancel recording.**

Cancel the ongoing recording. No callback will be triggered after cancellation.

## UploadRecordedFile

```csharp
UploadRecordedFile(string filePath)
```

**Upload voice file.**

Upload a local voice file.

| Parameter | Description |
| --- | --- |
| filePath | Local path of the voice file to upload. |

## DownloadRecordedFile

```csharp
int DownloadRecordedFile(string fileId, string filePath);
```

**Download voice file.**

| Parameter | Description |
| --- | --- |
| fileId | URL of the voice file. |
| filePath | Local path to save the downloaded file. The file extension must be `.ogg`. |

## PlayRecordedFile

```csharp
int PlayRecordedFile(string filePath);
```

**Play voice file.**

Play a local voice file.

| Parameter | Description |
| --- | --- |
| filePath | Local path to the voice file. |

## PlayRecordedFile

```csharp
int PlayRecordedFile(string filePath, ITMG_VOICE_TYPE voiceType);
```

**Play voice file.**

Play a local voice file with a specified voice effect.

| Parameter | Description |
| --- | --- |
| filePath | Local path to the voice file. |
| voiceType | Voice effect type. |

## StopPlayFile

**Stop playing voice file.**

Stop playback of the voice file. A callback is triggered upon completion.

## SpeechToText

```csharp
int SpeechToText(string fileID);
```

**Convert voice file to text.**

Convert a specified voice file to text.

| Parameter | Description |
| --- | --- |
| fileID | URL of the voice file. |

## SpeechToText

```csharp
int SpeechToText(string fileID, string speechLanguage);
```

**Convert voice file to text \(with language selection\).**

Specify the recognition language and optionally translate the recognized text into another language.

| Parameter | Description |
| --- | --- |
| fileID | URL of the voice file. The recording is stored on the server for 90 days. |
| speechLanguage | Language for speech recognition. |

## SpeechToText

```csharp
int SpeechToText(string fileID, string speechLanguage, string translatelanguage);
```

**Convert voice file to text \(with language selection\).**

Specify the recognition language and optionally translate the recognized text into another language.

| Parameter | Description |
| --- | --- |
| fileID | URL of the voice file. The recording is stored on the server for 90 days. |
| speechLanguage | Language for speech recognition. |
| translateLanguage | Language for translation of recognized text. |

## TranslateText

```csharp
int TranslateText(string text, string sourceLanguage, string translateLanguage);
```

**Translate text.**

Translate a segment of text, such as converting Chinese to English. The translation result is returned via callback.

| Parameter | Description |
| --- | --- |
| sourceLanguage | Language of the source text. Can be empty; backend will auto-detect the language. |
| text | Text to translate. Cannot be empty. Maximum length: 5000 characters. |
| translateLanguage | Target language for translation. Cannot be empty. Use English commas as separators, e.g., "cmn-Hans-CN,en-GB", "cmn-Hans-CN". |

## GetFileSize

```csharp
int GetFileSize(string filePath);
```

**Get voice file size.**

Retrieve the size of a local voice file.

| Parameter | Description |
| --- | --- |
| filePath | Local path to the voice file. |

## GetVoiceFileDuration

```csharp
int GetVoiceFileDuration(string filePath);
```

**Get voice file duration.**

Retrieve the duration of a local voice file in milliseconds.

| Parameter | Description |
| --- | --- |
| filePath | Local path to the voice file. |

## StartRecordingWithStreamingRecognition

```csharp
int StartRecordingWithStreamingRecognition(string filePath);
```

**Start streaming voice recognition.**

Begin streaming voice recognition. Real-time voice-to-text results are returned via callback. You can specify the recognition language and optionally translate the recognized text.

| Parameter | Description |
| --- | --- |
| filePath | Path to save the voice file. The file extension must be `.ogg`. If empty, the voice file will not be saved locally. |

## StartRecordingWithStreamingRecognition

```csharp
int StartRecordingWithStreamingRecognition(string filePath, string speechLanguage);
```

**Start streaming voice recognition.**

Begin streaming voice recognition. Real-time voice-to-text results are returned via callback. You can specify the recognition language and optionally translate the recognized text.

| Parameter | Description |
| --- | --- |
| filePath | Path to save the voice file. The file extension must be `.ogg`. If empty, the voice file will not be saved locally. |
| speechLanguage | Language for speech recognition. |

## StartRecordingWithStreamingRecognition

```csharp
int StartRecordingWithStreamingRecognition(string filePath, string speechLanguage, string translatelanguage);
```

**Start streaming voice recognition.**

Begin streaming voice recognition. Real-time voice-to-text results are returned via callback. You can specify the recognition language and optionally translate the recognized text.

| Parameter | Description |
| --- | --- |
| filePath | Path to save the voice file. The file extension must be `.ogg`. If empty, the voice file will not be saved locally. |
| speechLanguage | Language for speech recognition. |
| translateLanguage | Language for translation of recognized text. |

## SetPTTSourceLanguage

```csharp
int SetPTTSourceLanguage(string sourceLanguage);
```

**Set PTT source language.**

Set the language for recorded PTT voice files. The default language is Chinese.

| Parameter | Description |
| --- | --- |
| sourceLanguage | PTT source language. |

## TextToSpeech

```csharp
int TextToSpeech(int serialNumber, string text, string voiceName, string languageCode, float speakingRate);
```

**Convert text to speech.**

Convert a segment of text into a voice file. The API returns the voice file ID via callback. Use the download voice API to retrieve the voice file.

| Parameter | Description |
| --- | --- |
| languageCode | Target language. Cannot be empty. |
| serialNumber | Serial number. Returned in the callback. |
| speakingRate | Speech rate. Range: \[0.6-1.5\], 1 is normal speed. |
| text | Original text. Cannot be empty. Maximum length: 5000 characters. |
| voiceName | Voice type. English and Mandarin samples are provided. For other languages, please submit a ticket for support. |