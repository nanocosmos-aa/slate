---
title: WebRTC API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript: JavaScript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

WebRTC Public API Class Version 4.10.0.

# RTCUser API Reference

`RtcUser()` creates a new instance of the WebRTC public API class.

```javascript
var rtcUser = new RtcUser();
```

## Add Screen Capture Extension
### Method

`addScreenCaptureExtension(name)` adds a Screen Capture Extension to the RtcUser.

```javascript
// rtcUser instance of RtcUser
var name = 'nanoScreenCapture';
rtcUser.addScreenCaptureExtension(name);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
name | string | The name of the screen capture extension.

## Answer Call

`answerCall(remoteUserId)` answers a call with another user.

```javascript
// rtcUser instance of RtcUser
var remoteUserId = '49647969';
rtcUser.answerCall(remoteUserId);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
remoteUserId | string | The remote user id of the other user.

## Check Server

`checkServer(server)` checks the state of a webrtc server.

```javascript
// rtcUser instance of RtcUser
var server = 'https://rtc-lb.nanocosmos.de/p/webrtc'
rtcUser.checkServer(server);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
server | string | The url of the server.

### Fired Events

* ???

## Check Support

`checkSupport()` checks if nanoStream WebRTC is supported by current browser.

```javascript
RtcUser.checkSupport();
```

## Decline Call

`declineCall(remoteUserId)` declines a call with another user.

```javascript
// rtcUser instance of RtcUser
var remoteUserId = '49647969';
rtcUser.declineCall(remoteUserId);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
remoteUserId | string | The remote user id of the other user.

### Fired Events

* ???

## Enable Stats

`enableStats( [enable] [, interval])` enables to receive webrtc stats in a given time interval.

```javascript
// rtcUser instance of RtcUser
rtcUser.enableStats();
```

```javascript
// rtcUser instance of RtcUser
var enable = false;
rtcUser.enableStats(enable);
```

```javascript
// rtcUser instance of RtcUser
var enable = true;
var interval = 5000;
rtcUser.enableStats(enable, interval);
```

### Parameters

Name | Type | Argument | Default | Description
--------- | ------- | ----------- | --------- | ----------- 
enable | boolean | \<optional\> | true | A flag to enable webrtc stats.
interval | number | \<optional\> | 1000 | The interval time in milliseconds.

### Fired Events

* `ReceivedWebRTCStats`

## Enter Room

`enterRoom()` connects to the webrtc server and enters the specified room.

```javascript
// rtcUser instance of RtcUser
rtcUser.enterRoom();
```

### Parameters

Name | Type | Argument | Default | Description
--------- | ------- | ----------- | --------- | ----------- 
enable | boolean | \<optional\> | true | A flag to enable webrtc stats.
interval | number | \<optional\> | 1000 | The interval time in milliseconds.

### Fired Events

* `EnterRoomSuccess`
* `EnterRoomError`

## Get Devices

`getDevices(mediaIndexOrId)` gets all connected local video and audio devices

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
rtcUser.getDevices(mediaId);
```

```javascript
var mediaIndex = 0;
rtcUser.getDevices(mediaIndex);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
mediaIndexOrId | string \| number | The mediaId or the mediaIndex of a local media controller.

### Fired Events

* ???

## Hang Up Call

`hangUpCall(remoteUserId)` hangs up a call with another user.

```javascript
// rtcUser instance of RtcUser
var remoteUserId = '49647969';
rtcUser.hangUpCall(remoteUserId);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
remoteUserId | string | The remote user id of the other user.

## Inject External Media Stream

`injectExternalMediaStream(config)` mixes tracks (currently only audio) of an external MediaStream into the currently previewed local stream.

```javascript
// rtcUser instance of RtcUser
// externalStream instance of MediaStream (https://developer.mozilla.org/de/docs/Web/API/MediaStream) 
var data = {stream: externalStream, tracks: ['audio']};
rtcUser.injectExternalMediaStream(data);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>config</td>
			<td>object</td>
			<td>Config object with info on what to mix in.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>stream</td>
							<td>MediaStream</td>
							<td>The MediaStream containing the track(s) to mix in.</td>
						</tr>
						<tr>
							<td>tracks</td>
							<td>Array[string]</td>
							<td>Array with the types of tracks which should be injected (only 'audio' is supported at the moment).</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>

## Invoke Call

`invokeCall(remoteUserId)` invokes a call with another user.

```javascript
// rtcUser instance of RtcUser
var remoteUserId = '49647969';
rtcUser.invokeCall(remoteUserId);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
remoteUserId | string | The remote user id of the other user.

## In Screen Capture Available

`isScreenCaptureAvailable()` checks if a Screen Capture Extension was added via `addScreenCaptureExtension()`.

```javascript
// rtcUser instance of RtcUser
var name = 'nanoScreenCapture';
rtcUser.addScreenCaptureExtension(name);
// wait until api has registered extension:
setTimeout(function() {
    var hasScreenCapture = rtcUser.isScreenCaptureAvailable(); 
}, 1000);
```

## In Signed In

`isSignedIn() → {boolean}` checks if the `RtcUser` is connected with the webrtc server and signed in.

### Returned Value

**Type**: boolean

```javascript
// rtcUser instance of RtcUser
var isSignedIn = rtcUser.isSignedIn();
if (isSignedIn) {
    console.log('signed in');
} else {
    console.log('not signed in');
}
```

## Leave Room

`leaveRoom(forceSignOut)` disconnects from the webrtc server and leaves the specified room.

```javascript
// rtcUser instance of RtcUser
rtcUser.leaveRoom();
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
forceSignOut | boolean | Force stopping the broadcast.

### Fired Events

* `LeaveRoomSuccess`
* `LeaveRoomError`

## Mute Audio

`muteAudio(mediaIndexOrId, mute)` mutes / unmutes the audio of a local media controller.

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var mute = true;
rtcUser.muteAudio(mediaId, mute);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
mediaIndexOrId | string / number | The `mediaId` or the `mediaIndex` of a local media controller.
mute | boolean | Mute / unmute.

## Mute Video

`muteVideo(mediaIndexOrId, mute)` mutes/unmutes the video of a local media controller.

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var mute = true;
rtcUser.muteVideo(mediaId, mute);
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
mediaIndexOrId | string / number | The `mediaId` or the `mediaIndex` of a local media controller.
mute | boolean | Mute / unmute.

## Send Metadata

`sendMetaData(handlerName, jsonValues)` add live meta data to a broadcast stream.

```javascript
// rtcUser instance of RtcUser
rtcUser.sendMetaData('onMetaData', {myString: "hello", myInteger: 1234});
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
handlerName | 'onMetaData' / 'onCuePoint' | Name of the meta data handler. Other types are not supported.
jsonValues | object | The data to be sent. Parameter can contain a maximum object depth of 6.

## Set Audio Device

`setAudioDevice(mediaIndexOrId, config)` sets the input audio device for a local media controller.

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var config = {
    device: 0
};
rtcUser.setAudioDevice(mediaId, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaIndex = 0;
var config = {
    device: 0
};
rtcUser.setAudioDevice(mediaIndex, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var config = {
    device: true // auto device
};
rtcUser.setAudioDevice(mediaId, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaIndex = 0;
var config = {
    device: false // no video
};
rtcUser.setAudioDevice(mediaIndex, config);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>mediaIndexOrId</td>
			<td>string / number</td>
			<td>The mediaId or the mediaIndex of a local media controller.</td>
		</tr>
		<tr>
			<td>config</td>
			<td>object</td>
			<td>The config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>device</td>
							<td>boolean | number</td>
							<td>The value of the audio device, possible values: true (auto device), false (no audio), number (index of the audio device).</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>

## Set Config

`setConfig(server, userName, room [, token], serverUserName, serverPassword [, bintuApiKey])` sets the config for the RtcUser.

```javascript
// rtcUser instance of RtcUser
var server = 'https://rtc-lb.nanocosmos.de/p/1';
var userName = 'WebrtcChatter';
var room = 'myChatRoom';
var token = 'token-123';
var serverUserName = 'username';
var serverPassword = 'password';
var bintuApiKey = 'awdegfq3490puerg2w54zj2p0w4h46zphm694i0796';
rtcUser.setConfig(server, userName, room, token, serverUserName, serverPassword, bintuApiKey);
```

### Parameters

Name | Type | Argument | Description
--------- | ------- | ------- | -----------
server | string | | The url to the webrtc server.
userName | string | | The name of the RtcUser.
room | string | | The room to join.
token | string | \<optional\> | The name of the RtcUser.
serverUserName | string | | The username credential for the server.
serverPassword | string | | The password credential for the server.
bintuApiKey | string | \<optional\> | The bintu apikey for authentication.

## Set ICE Servers

`setIceServers(iceServers)` sets an array of turn/stun-servers for the peer-to-peer connection.

```javascript
// rtcUser instance of RtcUser
var iceServers = [
    {
        urls: [
            'turn:turn.myTurnServer.net:80?transport=udp'
        ],
        username: 'username',
        credential: 'password'
    },
    {
        urls: [
            'turn:turn.myTurnServer.net:80?transport=udp'
        ],
        username: 'username',
        credential: 'password'
    },
    {
        urls: [
            'stun:stun.l.google.com:19302'
        ]
    }
];
rtcUser.setIceServers(iceServers);
```

### Parameters

Name | Type | Argument | Description
--------- | ------- | ------- | -----------
iceServers | Array[object] | | The ice servers object.
iceServers[].urls | Array[string] | | An array of urls.
iceServers[].username | string | \<optional\> | The username for the ice servers if required.
iceServers[].credential | string | \<optional\> | The password for the ice servers if required.

## Set Optional Config

`setOptionalConfig(config)` sets optional config for the RtcUser.

```javascript
// rtcUser instance of RtcUser
var config = { 
    codecs: {
        videoCodec: 'H264'
    },
    bitrates: {                
        videoSendInitialBitrate: 500,
        videoSendBitrate: 1000
    }
};
rtcUser.setOptionalConfig(config);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>config</td>
			<td>object</td>
			<td>The config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>codecs</td>
							<td>object</td>
							<td>The codec object.</td>
						</tr>
						<tr>
							<td>&nbsp;</td>
							<td>&nbsp;</td>
							<td>
								<table>
				  					<thead>
   										<tr>
      										<th>Name</th>
      										<th>Type</th>
      										<th>Default</th>
      										<th>Description</th>
    									</tr>
  									</thead>
									<tbody>
										<tr>
											<td>videoCodec</td>
											<td>string</td>
											<td>'H264'</td>
											<td>The video codec to use (possible values: 'VP8', 'VP9', 'H264').</td>
										</tr>
									</tbody>
								</table>
							</td>
						</tr>
						<tr>
							<td>bitrates</td>
							<td>object</td>
							<td>The codec object.</td>
						</tr>
												<tr>
							<td>&nbsp;</td>
							<td>&nbsp;</td>
							<td>
								<table>
				  					<thead>
   										<tr>
      										<th>Name</th>
      										<th>Type</th>
      										<th>Default</th>
      										<th>Description</th>
    									</tr>
  									</thead>
									<tbody>
										<tr>
											<td>videoSendInitialBitrate</td>
											<td>string</td>
											<td>0</td>
											<td>The webrtc initial bitrate.</td>
										</tr>
										<tr>
											<td>videoSendBitrate</td>
											<td>string</td>
											<td>0</td>
											<td>The webrtc bitrate.</td>
										</tr>
									</tbody>
								</table>
							</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>

## Set Video Device

`setVideoDevice(mediaIndexOrId, config)` sets the input video device with config for a local media controller.

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var config = {
    device: 0,
    width: 640,
    height: 360,
    framerate: 30
};
rtcUser.setVideoDevice(mediaId, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaIndex = 0;
var config = {
    device: 0
};
rtcUser.setVideoDevice(mediaIndex, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var config = {
    device: true // auto device
};
rtcUser.setVideoDevice(mediaId, config);
```

```javascript
// rtcUser instance of RtcUser
var mediaIndex = 0;
var config = {
    device: false // no video
};
rtcUser.setVideoDevice(mediaIndex, config);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>mediaIndexOrId</td>
			<td>string | number</td>
			<td>The mediaId or the mediaIndex of a local media controller.</td>
		</tr>
		<tr>
			<td>config</td>
			<td>object</td>
			<td>The config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Argument</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>device</td>
							<td>boolean / number</td>
							<td>&nbsp;</td>
							<td>The value of the video device, possible values: true (auto device), false (no video), number (index of the video device).</td>
						</tr>
						<tr>
							<td>width</td>
							<td>number</td>
							<td>optional</td>
							<td>The input width (only if device will be set by index).</td>
						</tr>
						<tr>
							<td>height</td>
							<td>number</td>
							<td>optional</td>
							<td>The input height (only if device will be set by index).</td>
						</tr>
						<tr>
							<td>framerate</td>
							<td>number</td>
							<td>optional</td>
							<td>The input framerate (only if device will be set by index).</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>

## Start Broadcast

`startBroadcast(config)` starts a broadcast to a rtmp ingest with transcoding configs.

```javascript
// rtcUser instance of RtcUser
var broadcastConfig = {
    transcodingTargets: {
        output: 'rtmp://myIngestServer.com:1935/live/webrtcBroadcast',
        videobitrate: 500000,
        audiobitrate: 64000,
        framerate: 30,
        dropframes: '0',
        icecast_audio: '0',
        rtmpconnectinfo: {"key1":"value1","key2":7.5,"key3":false} 
    }
};
rtcUser.startBroadcast(broadcastConfig);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>config</td>
			<td>object</td>
			<td>The config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>transcodingTargets</td>
							<td>object</td>
							<td>The transcoding config object.</td>
						</tr>
						<tr>
							<td>&nbsp;</td>
							<td>&nbsp;</td>
							<td>
								<table>
				  					<thead>
   										<tr>
      										<th>Name</th>
      										<th>Type</th>
      										<th>Argument</th>
      										<th>Default</th>
      										<th>Description</th>
    									</tr>
  									</thead>
									<tbody>
										<tr>
											<td>output</td>
											<td>string</td>
											<td>&nbsp;</td>
											<td>&nbsp;</td>
											<td>The rtmp ingest url for the first stream.</td>
										</tr>
										<tr>
											<td>streamname</td>
											<td>string</td>
											<td>optional</td>
											<td>null</td>
											<td>Optional streamname. Use if you want to pass output and streamname seperately.</td>
										</tr>
										<tr>
											<td>videobitrate</td>
											<td>number</td>
											<td>optional</td>
											<td>null</td>
											<td>The video bitrate for the transcode of the first stream.</td>
										</tr>
										<tr>
											<td>audiobitrate</td>
											<td>number</td>
											<td>optional</td>
											<td>null</td>
											<td>The audio bitrate for the transcode of the first stream.</td>
										</tr>
										<tr>
											<td>framerate</td>
											<td>number</td>
											<td>optional</td>
											<td>null</td>
											<td>The framerate for the transcode of the first stream.</td>
										</tr>
										<tr>
											<td>dropframes</td>
											<td>string</td>
											<td>optional</td>
											<td>null</td>
											<td>A flag to enable frame dropping (possible values: '0', '1').</td>
										</tr>
										<tr>
											<td>h264passthrough</td>
											<td>string</td>
											<td>optional</td>
											<td>null</td>
											<td>A flag to enable transmuxing without transcoding if video codec 'H264' is used (possible values: '0', '1').</td>
										</tr>
										<tr>
											<td>icecast_audio</td>
											<td>string</td>
											<td>optional</td>
											<td>null</td>
											<td>A flag to enable embedding of an icecast audio stream, normal audio will be ignored (possible values: '0', '1').</td>
										</tr>
										<tr>
											<td>rtmpconnectinfo</td>
											<td>string</td>
											<td>optional</td>
											<td>null</td>
											<td>Data to be send with the rtmp streams "onconnect". Pass flat object with key value pairs, hierarchies are not supported.</td>
										</tr>
									</tbody>
								</table>
							</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>

### Fired Events

* `StartBroadcastSuccess`
* `StartBroadcastError`

## Start Preview

`startPreview(mediaIndexOrId, videoDeviceConfig, audioDeviceConfig, elementId, useWebView)` starts the preview of a local media controller.

```javascript
// rtcUser instance of RtcUser
var mediaId = 'local';
var videoDeviceConfig = {
    device: 0,
    width: 640,
    height: 360,
    framerate: 30,
    source: 'camera'
};
var audioDeviceConfig = {
    device: 0
};
var useWebView = true;
rtcUser.startPreview(mediaId, videoDeviceConfig, audioDeviceConfig, useWebView);
```

### Parameters

<table>
  	<thead>
   		<tr>
      		<th>Name</th>
      		<th>Type</th>
      		<th>Description</th>
    	</tr>
  	</thead>
	<tbody>
		<tr>
			<td>mediaIndexOrId</td>
			<td>string / number</td>
			<td>The mediaId or the mediaIndex of a local media controller.</td>
		</tr>
		<tr>
			<td>videoDeviceConfig</td>
			<td>object</td>
			<td>The video config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>device</td>
							<td>int</td>
							<td>Device id to use.</td>
						</tr>
						<tr>
							<td>width</td>
							<td>int</td>
							<td>Video width.</td>
						</tr>
						<tr>
							<td>height</td>
							<td>int</td>
							<td>Video height.</td>
						</tr>
						<tr>
							<td>framerate</td>
							<td>int</td>
							<td>Video framerate.</td>
						</tr>
						<tr>
							<td>source</td>
							<td>String</td>
							<td>The video source to be requested valid parameters: 'camera' | 'screen'.</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
		<tr>
			<td>audioDeviceConfig</td>
			<td>object</td>
			<td>The audio config object.</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<table>
				  	<thead>
   						<tr>
      						<th>Name</th>
      						<th>Type</th>
      						<th>Description</th>
    					</tr>
  					</thead>
					<tbody>
						<tr>
							<td>device</td>
							<td>int</td>
							<td>Device id to use.</td>
						</tr>
					</tbody>
				</table>
			</td>
		</tr>
		<tr>
			<td>elementId</td>
			<td>string</td>
			<td>The id of a video element to pass in the requested stream directly.</td>
		</tr>
		<tr>
			<td>useWebView</td>
			<td>boolean</td>
			<td>A flag to indicate that a WebView is used; default value: false.</td>
		</tr>
	</tbody>
</table>

### Fired Events

* `StartPreviewSuccess`
* `StartPreviewError`

## Stop Broadcast

`stopBroadcast(forceSignOut)` stop a running broadcast.

```javascript
// rtcUser instance of RtcUser
rtcUser.stopBroadcast();
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
forceSignOut | boolean | Force stopping the broadcast.

### Fired Events

* `StopBroadcastSuccess	`
* `StopBroadcastError`

## Stop Preview

`stopPreview(mediaIndexOrId)` stops the preview of a local media controller.

```javascript
// rtcUser instance of RtcUser
rtcUser.stopBroadcast();
```

### Parameters

Name | Type | Description
--------- | ------- | -----------
mediaIndexOrId | string / number | The mediaId or the mediaIndex of a local media controller.

### Fired Events

* `StopPreviewSuccess`
* `StopPreviewError`

# Example

# FAQ

