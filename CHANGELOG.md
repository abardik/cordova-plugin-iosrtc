#### Version 5.0.4

* Fix MediaStream.create false positive "ERROR: video track not added" and "ERROR: audio track not added" cause the rtcMediaStream already has them internaly trigger by getUserMedia.
* Detect deprecated callbacks usage and throw Error instead of been silent to assist 5.0.1 to 5.0.2 migration from WebRTC callback RTCPeerConnection.(createOffer|createAnswer|setLocalDescription|setRemoteDescription|addIceCandidate|getStats) and getUserMedia API.
* Reset enumerateDevices videoinput order with front camera first to keep legacy behavior.
* Use safeAreaLayoutGuide for ios 11 and NSLayoutConstraint for ios 10 to fix elementView bad position depending status bar visibility ([PR #367](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/367) by @hthetiot).
* Recognize when a video receives a new srcObject and re-render it ([PR #367](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/395) by @SejH).

#### Version 5.0.3

* Fix MediaStream.active getter issue.
* Fix cordova.plugins.iosrtc.observeVideo MutationObserver issue with srcObject using loadstart and emptied events that does get triggered.
* Add NSBluetoothAlwaysUsageDescription to Info.plist for wireless headphones and microphone consent.
* Deprecate usage of `video.src = URL.createObjectURL(stream)` in favor of `video.srcObject = stream` only MediaStream are not Blob anymore. ([PR #388](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/388) by @hthetiot).
* Update audio input priority to Wired microphone > Wireless microphone > built-in microphone. ([PR #387](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/387) by @CSantosM).
* Add possible missing argument for parameter 'mode' in call on audioSession.setCategory.

#### Version 5.0.2

* Remove WebRTC callback based API for RTCPeerConnection.(createOffer|createAnswer|setLocalDescription|setRemoteDescription|addIceCandidate|getStats) and getUserMedia.
* Set default deployment target to 10.2
* Implement partial RTCPeerConnection.(getSenders|getReceivers|addTrack|removeTrack)
* Fix webrtc-adapter external library support
* Fix Blob prototype pollution
* Extend native MediaStream instead of using Blob
* Fix RTCPeerConnection.setLocalDescription() and other methods which take SDP as input now directly accept an object
* Upgrade packages debug to ^4.1.1 and yaeti to ^1.0.2
* Add cordova.plugins.iosrtc.getUserMedia MediaTrackConstraints.(video|audio).deviceId.(exact|ideal) support ([PR #374](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/374) by @CSantosM).
* Add cordova.plugins.iosrtc.getMediaDevices bluetooth and wired audio devices support ([PR #374](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/374) by @CSantosM).
* fix TypeError: undefined is not an object (evaluating 'stream.id') when removing stream [PR #383](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/383) by @hthetiot via @l7s).

#### Version 5.0.1

* fix typo on iosrtcPlugin.swift

#### Version 5.0.0

* fix README.md
* Convert syntax to Swift 4.2
* Uncomment, and fix, onGetStatsCallback closure
* Update NPM dependencies
* Add Travis build (Ionic, Cordova, Browser, Android, iOS Xcode 10.2)
* Fix gulp browserify caused by old vinyl package version
* Migrate from jscs to eslint to fix vulnerabilities reported by npm audit

#### Version 4.0.2

* `getUserMedia` constraints: Allow `sourceId` (rather than just `deviceId`) to make adapter.js happy (#282).


#### Version 4.0.1

* Let `addIceCandidate()` be called with a `RTCIceCandidateInit` object as argument (as per the latest WebRTC spec) rather than mandating a `RTCIceCandidate` instance.


#### Version 4.0.0

* Moved the repository over to its new home with the Basque VoIP Mafia
* Fix compatibility with "--browserify" cordova option
* Convert syntax to Swift 3
* Remove rtcninja integration
* Remove selectAudioOutput function
* Add convenience Makefile
* Update documentation


#### Version 3.2.2

* Fix promise implementation of RTCPeerConnection.getStats


#### Version 3.2.1

* Fix emitting "connected" stream event for local streams when using getUserMedia with promises.


#### Version 3.2.0

* Add support for RTCPeerConnection.getStats ([PR #163](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/163) by @oNaiPs)

* Set default deployment target to 9.0

* Document iOS 10 specific stuff

* Fix crash if RTCPeerConnection.close() is called twice

* Data channel improvements

* Updated documentation


#### Version 3.1.0

* Implement `RTCPeerConnection.createDTMFSender()` ([PR #189](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/189) by @saghul).

* Make `ios-websocket-hack.js` more reliable.


#### Version 3.0.1

* Fix positioning video elements using `z-index` and allow pure HTML on top of `<video>` elements ([PR #179](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/179) by @saghul and @1N50MN14).
 
* Improve `ios-websocket-hack.js` ([PR #138](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/138) by @apparition47).


#### Version 3.0.0

* Upgrade to `cordova-ios` 4 ([PR #159](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/159) by @apparition47).

* Swift: Use closure syntax for weak and unowned vars ([PR #160](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/160) by @oNaiPs).

* Swift: Sanitize arguments given to `NSLog()` ([issue #157](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/157)).

* `MediaDeviceInfo`: Add deprecated `facing` property ("front", "back" or "unknown") and update `kind` ("audio"/"video" become "audioinput"/"videoinput") ([issue #155](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/155)).

* Update `libwebrtc` to revision 12558 ([issue #169](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/169)).


#### Version 2.2.4

* Fix crash ([issue #144](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/144)).

* Update NPM dependencies.


#### Version 2.2.3

* Enable iOS native H.264 encoder/decoder.

* `RTCDataChannel`: Allow empty `label` ([issue #124](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/124)).

* Update [yaeti](https://www.npmjs.com/package/yaeti) dependency ([issue #123](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/123)).

* Fix retain on `pluginMediaStreamTrack` does not allow camera/mic to be freed ([PR #126](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/126)). Credits to @oNaiPs.

* Allow a handled video element to be removed from the DOM and added again later ([PR #127](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/127)). Credits to @oNaiPs.


#### Version 2.2.2

* Update `libwebrtc` to revision 11063 so `MediaStream` events (`onaddtrack` and `onremovetrack`) work again ([issue #95](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/95)).


#### Version 2.2.1

* `getUserMedia()`: Fire `errback` if given video constraints are not satisfied.


#### Version 2.2.0

* Move from `getMediaDevices()` to `enumerateDevices()`.
* Implement video constraints in `getUserMedia()`: `deviceId`, `width.min`, `width.max`, `height.min`, `height.max`, `frameRate`, `frameRate.min`, `frameRate.max`).
* Update deps and build on Node >= 4.


#### Version 2.1.0

* Update *libwebrtc* to latest revision (rev 10800).
* Enble iOS native H264 codec.


#### Version 2.0.2

* Enable CSS padding (thanks to @saghul) ([pull request #89](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/89)).


#### Version 2.0.1

* Don't crash if user or iOS settings deny access lo local audio/video devices ([issue #73](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/73)).


#### Version 2.0.0

* Swift 2.0 is here! Credits to @saghul for his [pull request](https://github.com/cordova-rtc/cordova-plugin-iosrtc/pull/70).
* `extra/hooks/iosrtc-swift-support.js`: Set `BUILD_VERSION` to 7.0.


#### Version 1.4.5

* Add `cordova.plugins.iosrtc.observeVideo(video)` API for the plugin to handle `<video>` elements not yet in the DOM ([issue #49](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/49)).


#### Version 1.4.4

* Support CSS `border-radius` property in HTML video elements.


#### Version 1.4.3

* Make private properties more private ([issue #34](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/34)).


#### Version 1.4.2

* Use [yaeti](https://github.com/ibc/yaeti) module as `EventTarget` shim.


#### Version 1.4.1

* Release `MediaStreamRenderer` and revert `<video>` properties when the attached `MediaStream` emits "inactive" ([issue #27](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/27)).


#### Version 1.4.0

* Implemented some `<video>` properties such as `readyState`, `videoWidth` and `videoHeight` ([issue #25](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/25)).
* Building simplified for both Cordova CLI and Xcode by providing a single ["hook"](extra/hooks/iosrtc-swift-support.js) the user must add into his Cordova application (check the [Building](docs/Building.md) documentation for further details).


#### Version 1.3.3

* CSS `object-fit: none` properly implemented (don't clip the video).


#### Version 1.3.2

* CSS [object-fit](https://css-tricks.com/almanac/properties/o/object-fit/) property implemented in `<video>` elements ([issue #23](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/23)).


#### Version 1.3.1

* Stop "error" event propagation in `<video>` element when attaching a `MediaStream` to it ([issue #22](https://github.com/cordova-rtc/cordova-plugin-iosrtc/issues/22)).


#### Version 1.3.0

* Plugin moved to [NPM](https://www.npmjs.com/package/cordova-plugin-iosrtc) registry and plugin ID renamed to *cordova-plugin-iosrtc*.


#### Version 1.2.8

* `iosrtc.registerGlobals()` also generates `window.webkitRTCPeerConnection` and `navigator.webkitGetUserMedia()` for backwards compatibility with WebRTC JavaScript wrappers/adapters that assume browser vendor prefixes (`webkit`, `moz`) in the underlying WebRTC API.



