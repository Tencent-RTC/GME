# API概览

## Basic Features

| Function List | Description |
| --- | --- |
| [GetInstance](ITMGContext.md#getinstance) | Get the GME SDK instance \(singleton\). |
| [SetLibraryPath](ITMGContext.md#setlibrarypath) | Specify the path for native library files. |
| [CreateSubInstance](ITMGContext.md#createsubinstance) | Create a GME sub-instance. |
| [DestroySubInstance](ITMGContext.md#destroysubinstance) | Destroy a GME sub-instance. |
| [SetRegion](ITMGContext.md#setregion) | Configure the access point \(deprecated\). |
| [Init](ITMGContext.md#init) | Initialize the GME SDK. |
| [Poll](ITMGContext.md#poll) | Trigger event callback. |
| [Pause](ITMGContext.md#pause) | Pause the SDK. |
| [Resume](ITMGContext.md#resume) | Resume the SDK. |
| [Uninit](ITMGContext.md#uninit) | Uninitialize the GME SDK. |
| [SetScene](ITMGContext.md#setscene) | Set the application scenario. |
| [SetAudioRole](ITMGContext.md#setaudiorole) | Switch user role. |
| [SetRangeAudioMode](ITMGContext.md#setrangeaudiomode) | Configure range audio mode. |
| [SetRangeAudioTeamID](ITMGContext.md#setrangeaudioteamid) | Set TeamID for range audio. |
| [EnterRoom](ITMGContext.md#enterroom) | Join a voice room. |
| [ExitRoom](ITMGContext.md#exitroom) | Leave a voice room. |
| [IsRoomEntered](ITMGContext.md#isroomentered) | Check if the user is in a voice room. |
| [SetLogLevel](ITMGContext.md#setloglevel) | Set log output level. |
| [SetLogPath](ITMGContext.md#setlogpath) | Specify the log file save path. |
| [GetLogPath](ITMGContext.md#getlogpath) | Retrieve the log file save path. |
| [GetSDKVersion](ITMGContext.md#getsdkversion) | Get the GME SDK version. |
| [SetAppVersion](ITMGContext.md#setappversion) | Set the app version. |
| [ShowDebugView](ITMGContext.md#showdebugview) | Display the dashboard. |
| [GetRoom](ITMGContext.md#getroom) | Get the room class instance. |
| [GetPttCtrl](ITMGContext.md#getpttctrl) | Get the offline voice class instance. |
| [GetAudioCtrl](ITMGContext.md#getaudioctrl) | Get the audio control class instance. |
| [GetAudioEffectCtrl](ITMGContext.md#getaudioeffectctrl) | Get the audio effect control class instance. |
| [SetRecvMixStreamCount](ITMGContext.md#setrecvmixstreamcount) | Set the maximum number of mixed streams. |
| [SetAdvanceParams](ITMGContext.md#setadvanceparams) | Configure advanced feature parameters. |
| [GetAdvanceParams](ITMGContext.md#getadvanceparams) | Retrieve advanced feature parameter values. |
| [CheckMicPermission](ITMGContext.md#checkmicpermission) | Check microphone permissions. |

## Audio Control

| Function List | Description |
| --- | --- |
| [EnableMic](ITMGAudioCtrl.md#enablemic) | Enable or disable the microphone. |
| [GetMicState](ITMGAudioCtrl.md#getmicstate) | Get the microphone status. |
| [EnableSpeaker](ITMGAudioCtrl.md#enablespeaker) | Enable or disable the speaker. |
| [GetSpeakerState](ITMGAudioCtrl.md#getspeakerstate) | Get the speaker status. |
| [EnableAudioCaptureDevice](ITMGAudioCtrl.md#enableaudiocapturedevice) | Enable the audio capture device. |
| [IsAudioCaptureDeviceEnabled](ITMGAudioCtrl.md#isaudiocapturedeviceenabled) | Get the audio capture device status. |
| [EnableAudioPlayDevice](ITMGAudioCtrl.md#enableaudioplaydevice) | Enable or disable the playback device. |
| [IsAudioPlayDeviceEnabled](ITMGAudioCtrl.md#isaudioplaydeviceenabled) | Get the playback device status. |
| [EnableAudioSend](ITMGAudioCtrl.md#enableaudiosend) | Enable or disable audio uplink. |
| [IsAudioSendEnabled](ITMGAudioCtrl.md#isaudiosendenabled) | Get audio uplink status. |
| [EnableAudioRecv](ITMGAudioCtrl.md#enableaudiorecv) | Enable or disable audio downlink. |
| [IsAudioRecvEnabled](ITMGAudioCtrl.md#isaudiorecvenabled) | Get audio downlink status. |
| [SetMicVolume](ITMGAudioCtrl.md#setmicvolume) | Adjust microphone volume gain. |
| [GetMicVolume](ITMGAudioCtrl.md#getmicvolume) | Get microphone volume gain. |
| [SetSpeakerVolume](ITMGAudioCtrl.md#setspeakervolume) | Adjust speaker volume gain. |
| [GetSpeakerVolume](ITMGAudioCtrl.md#getspeakervolume) | Get speaker volume gain. |
| [SetSpeakerVolumeByUserID](ITMGAudioCtrl.md#setspeakervolumebyuserid) | Set volume gain for a specific user in the room. |
| [GetSpeakerVolumeByUserID](ITMGAudioCtrl.md#getspeakervolumebyuserid) | Get the volume gain for a specific user in the room. |
| [EnableLoopBack](ITMGAudioCtrl.md#enableloopback) | Enable or disable audio loopback. |
| [SetLoopBackVolume](ITMGAudioCtrl.md#setloopbackvolume) | Set loopback volume. |
| [AddAudioBlackList](ITMGAudioCtrl.md#addaudioblacklist) | Mute a user in the room. |
| [RemoveAudioBlackList](ITMGAudioCtrl.md#removeaudioblacklist) | Unmute a user in the room. |
| [IsUserIDInAudioBlackList](ITMGAudioCtrl.md#isuseridinaudioblacklist) | Check if a user is muted. |
| [InitSpatializer](ITMGAudioCtrl.md#initspatializer) | Initialize the 3D audio processor. |
| [EnableSpatializer](ITMGAudioCtrl.md#enablespatializer) | Enable or disable 3D audio effects. |
| [IsEnableSpatializer](ITMGAudioCtrl.md#isenablespatializer) | Get the current 3D audio effect status. |
| [GetMicListCount](ITMGAudioCtrl.md#getmiclistcount) | Get the number of microphone devices \(desktop only\). |
| [GetMicList](ITMGAudioCtrl.md#getmiclist) | List microphone devices \(desktop only\). |
| [SelectMic](ITMGAudioCtrl.md#selectmic) | Select a microphone device \(desktop only\). |
| [GetCurrentMic](ITMGAudioCtrl.md#getcurrentmic) | Get the currently selected microphone device \(desktop only\). |
| [GetSpeakerListCount](ITMGAudioCtrl.md#getspeakerlistcount) | Get the number of speaker devices \(desktop only\). |
| [GetSpeakerList](ITMGAudioCtrl.md#getspeakerlist) | List speaker devices \(desktop only\). |
| [SelectSpeaker](ITMGAudioCtrl.md#selectspeaker) | Select a speaker device \(desktop only\). |
| [GetCurrentSpeaker](ITMGAudioCtrl.md#getcurrentspeaker) | Get the currently selected speaker device \(desktop only\). |
| [EnableCustomAudioCapture](ITMGAudioCtrl.md#enablecustomaudiocapture) | Enable custom audio capture mode. |
| [SetAudioRoute](ITMGAudioCtrl.md#setaudioroute) | Configure audio routing. |
| [SendCustomAudioData](ITMGAudioCtrl.md#sendcustomaudiodata) | Send custom audio data to the SDK. |
| [EnableCustomAudioRendering](ITMGAudioCtrl.md#enablecustomaudiorendering) | Enable custom audio playback. |
| [GetCustomAudioRenderingFrame](ITMGAudioCtrl.md#getcustomaudiorenderingframe) | Retrieve playable audio data. |
| [TrackingVolume](ITMGAudioCtrl.md#trackingvolume) | Enable volume callback. |
| [StopTrackingVolume](ITMGAudioCtrl.md#stoptrackingvolume) | Disable volume callback. |
| [GetMicLevel](ITMGAudioCtrl.md#getmiclevel) | Get real-time microphone volume. |
| [GetSpeakerLevel](ITMGAudioCtrl.md#getspeakerlevel) | Get real-time speaker volume. |
| [GetSendStreamLevel](ITMGAudioCtrl.md#getsendstreamlevel) | Get real-time audio uplink volume. |
| [GetRecvStreamLevel](ITMGAudioCtrl.md#getrecvstreamlevel) | Get real-time audio downlink volume for other users in the room. |
| [StartMicDeviceTest](ITMGAudioCtrl.md#startmicdevicetest) | Start microphone device test \(desktop only\). |
| [StopMicDeviceTest](ITMGAudioCtrl.md#stopmicdevicetest) | Stop microphone device test \(desktop only\). |
| [StartSpeakerDeviceTest](ITMGAudioCtrl.md#startspeakerdevicetest) | Start speaker device test \(desktop only\). |
| [StopSpeakerDeviceTest](ITMGAudioCtrl.md#stopspeakerdevicetest) | Stop speaker device test \(desktop only\). |
| [SetAudioFrameCallback](ITMGAudioCtrl.md#setaudioframecallback) | Set custom audio data callback. |

## Audio Effects and Background Music

| Function List | Description |
| --- | --- |
| [StartPlayMusic](ITMGAudioEffectCtrl.md#startplaymusic) | Start background music playback. |
| [StopPlayMusic](ITMGAudioEffectCtrl.md#stopplaymusic) | Stop background music playback. |
| [PausePlayMusic](ITMGAudioEffectCtrl.md#pauseplaymusic) | Pause background music playback. |
| [ResumePlayMusic](ITMGAudioEffectCtrl.md#resumeplaymusic) | Resume background music playback. |
| [IsMusicPlayEnd](ITMGAudioEffectCtrl.md#ismusicplayend) | Check if background music playback has ended. |
| [SetAllMusicVolume](ITMGAudioEffectCtrl.md#setallmusicvolume) | Set local and remote volume for all background music tracks. |
| [SetMusicPublishVolume](ITMGAudioEffectCtrl.md#setmusicpublishvolume) | Set remote volume for a specific background music track. |
| [GetMusicPublishVolume](ITMGAudioEffectCtrl.md#getmusicpublishvolume) | Get remote volume for a specific background music track. |
| [SetMusicPlayoutVolume](ITMGAudioEffectCtrl.md#setmusicplayoutvolume) | Set local volume for a specific background music track. |
| [GetMusicPlayoutVolume](ITMGAudioEffectCtrl.md#getmusicplayoutvolume) | Get local volume for a specific background music track. |
| [SetMusicPitch](ITMGAudioEffectCtrl.md#setmusicpitch) | Adjust background music pitch. |
| [GetMusicDurationInMS](ITMGAudioEffectCtrl.md#getmusicdurationinms) | Get the total duration of background music \(milliseconds\). |
| [GetMusicCurrentPosInMS](ITMGAudioEffectCtrl.md#getmusiccurrentposinms) | Get the current playback position of background music \(milliseconds\). |
| [SeekMusicToPosInTime](ITMGAudioEffectCtrl.md#seekmusictoposintime) | Set the playback position of background music \(milliseconds\). |
| [EnableMusicPublish](ITMGAudioEffectCtrl.md#enablemusicpublish) | Publish background music for the specified sound\_id to remote users. |
| [EnableMusicPlayout](ITMGAudioEffectCtrl.md#enablemusicplayout) | Play background music for the specified sound\_id locally. |
| [SetVoiceType](ITMGAudioEffectCtrl.md#setvoicetype) | Apply voice changing effects. |
| [SetKaraokeType](ITMGAudioEffectCtrl.md#setkaraoketype) | Apply vocal reverb effects. |
| [StartRecord](ITMGAudioEffectCtrl.md#startrecord) | Start audio recording. |
| [StopRecord](ITMGAudioEffectCtrl.md#stoprecord) | Stop audio recording. |
| [StartSystemAudioLoopback](ITMGAudioEffectCtrl.md#startsystemaudioloopback) | Enable system audio capture. |
| [StopSystemAudioLoopback](ITMGAudioEffectCtrl.md#stopsystemaudioloopback) | Disable system audio capture. |
| [SetSystemAudioLoopbackVolume](ITMGAudioEffectCtrl.md#setsystemaudioloopbackvolume) | Set system audio capture volume. |

## Audio Room

| Function List | Description |
| --- | --- |
| [GetRoomID](ITMGRoom.md#getroomid) | Get the voice room ID. |
| [ChangeRoomType](ITMGRoom.md#changeroomtype) | Change the user's room audio type. |
| [GetRoomType](ITMGRoom.md#getroomtype) | Get the current room audio type. |
| [StartRoomSharing](ITMGRoom.md#startroomsharing) | Start cross-room co-hosting call. |
| [StopRoomSharing](ITMGRoom.md#stoproomsharing) | End cross-room co-hosting call. |
| [SwitchRoom](ITMGRoom.md#switchroom) | Switch rooms instantly. |
| [SendCustomData](ITMGRoom.md#sendcustomdata) | Send custom messages. |
| [StopSendCustomData](ITMGRoom.md#stopsendcustomdata) | Stop sending custom messages. |
| [UpdateAudioRecvRange](ITMGRoom.md#updateaudiorecvrange) | Set the audio receive distance range. |
| [UpdateSpatializerRecvRange](ITMGRoom.md#updatespatializerrecvrange) | Set 3D audio attenuation distance. |
| [UpdateSelfPosition](ITMGRoom.md#updateselfposition) | Update the user's sound source orientation and coordinates in the specified room. |
| [UpdateOtherPosition](ITMGRoom.md#updateotherposition) | Update the spatial coordinates of a remote user. |
| [SendSEIMsg](ITMGRoom.md#sendseimsg) | Send custom messages via SEI channel. |
| [GetAITranscriberManager](ITMGRoom.md#getaitranscribermanager) | Get the AI transcriber manager instance. |

## Offline Voice

| Function List | Description |
| --- | --- |
| [ApplyPTTAuthbuffer](ITMGPTT.md#applypttauthbuffer) | Apply authentication credentials. |
| [SetMaxMessageLength](ITMGPTT.md#setmaxmessagelength) | Set the maximum voice message duration. |
| [StartRecording](ITMGPTT.md#startrecording) | Start voice recording. |
| [StopRecording](ITMGPTT.md#stoprecording) | Stop voice recording. |
| [CancelRecording](ITMGPTT.md#cancelrecording) | Cancel voice recording. |
| [UploadRecordedFile](ITMGPTT.md#uploadrecordedfile) | Upload a voice file. |
| [DownloadRecordedFile](ITMGPTT.md#downloadrecordedfile) | Download a voice file. |
| [PlayRecordedFile](ITMGPTT.md#playrecordedfile) | Play a voice file. |
| [StopPlayFile](ITMGPTT.md#stopplayfile) | Stop voice file playback. |
| [SpeechToText](ITMGPTT.md#speechtotext) | Convert a voice file to text. |
| [TranslateText](ITMGPTT.md#translatetext) | Text translation API. |
| [GetFileSize](ITMGPTT.md#getfilesize) | Get the file size of a voice recording. |
| [GetVoiceFileDuration](ITMGPTT.md#getvoicefileduration) | Get the duration of a voice file. |
| [StartRecordingWithStreamingRecognition](ITMGPTT.md#startrecordingwithstreamingrecognition) | Start streaming voice recognition. |
| [SetPTTSourceLanguage](ITMGPTT.md#setpttsourcelanguage) | Set the source language for PTT. |
| [TextToSpeech](ITMGPTT.md#texttospeech) | Text-to-speech API. |