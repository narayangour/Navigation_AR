# Changelog

## v0.11.0

### Vision
- Added `Germany` country
- Added new `SignTypes`:
`InformationCarWashing`, `InformationBusStop`, `RegulatoryPedestriansCrossingUp`,
`RegulatoryPedestriansCrossingDown`, `InformationAutoService`, `InformationFood`,
`InformationTown`, `InformationTownEnd`, `RegulatoryControl`,
`RegulatoryDoubleUTurn`, `SpeedLimitZone`, `SpeedLimitEndZone`
- Added an ability to work with image data as direct `ByteBuffer`'s
- Added an ability to copy `Image` pixel data to `ByteArray`/`ByteBuffer`
- Added proguard consumer config to allow obfuscation on client side
- Added `armeabi-v7a` ABI to abiFilters to build older architecture
- Fixed a crash happening on `VisionManager.destroy`

### Ar
- Added new `Fence` AR style
- Added `FenceVisualParams` class and `VisionArView.setFenceVisualParams` method for customization of `Fence` rendering
- Added `VisionArView.setArQuality` method to set overall quality of AR objects
- Added `VisionArView.setFenceVisible`/`VisionArView.isFenceVisible`/
`VisionArView.setLaneVisible`/`VisionArView.isLaneVisible` to manage displayed AR features
- Added `VisionArView.onPause` method, that should be called when view is
hidden or detached

## v0.10.1

- Fixed bug with session not being recorded

## v0.10.0

- Added support for Snapdragon 855
- `VisionView` renders now with OpenGL ES
- Changed public API of `VisionView`
- Changed `VisionView` lifecycle if `VisionManager` is set
- Change internal camera lifecycle
- Fixed memory leak on `VisionManager.destroy()`
- Fixed gpu memory leak
- Fixed issues with destroying VisionManager
- Renamed `VisualizationMode.Detections` to `VisualizationMode.Detection`
- Added detection of construction cones
- Improved quality of detection/segmentation, especially at night
- Improved segmentation, now it's more focused on road specific elements. New segmentation model recognizes the following classes: Crosswalk, Hood, MarkupDashed, MarkupDouble, MarkupOther, MarkupSolid, Other, Road, RoadEdge, Sidewalk

## v0.9.0

### Vision
- Added to `VisionManager` method `start()`, property `visionEventsListener`. `visionEventsListener` is held as a weak reference.
- Added to `VisionReplayManager` method `start()`, property `visionEventsListener`. `visionEventsListener` is held as a weak reference.
- Deprecated `VisionManager` method `start(VisionEventsListener)`
- Deprecated `VisionReplayManager` method `start(VisionEventsListener)`
- Added new `SignType`s: `RegulatoryKeepLeftPicture`, `RegulatoryKeepLeftText`,`AheadSpeedLimit`,`WarningSpeedLimit`,`RegulatoryNoUTurnRight`,`WarningTurnRightOnlyArrow`

### Ar
- Added to `VisionArManager` method `create(BaseVisionManager)`, property `visionArEventsListener`. `visionArEventsListener` is held as a weak reference.
- Deprecated `VisionArManager` method `create(BaseVisionManager, VisionArEventsListener)`
- Changed `Ar Lane` API, `VisionArView`: `setArManager(VisionArManager)`
- Removed from `VisionArView` following methods: `onArCameraUpdated`, `onArLaneUpdated`, `onNewFrame`, `onNewCameraParameters`
- Changed `VisionArView` doesn't implement `VideoSourceListener` and `VisionArEventsListener`
- Changed `Ar Lane` appearance
- Moved `Ar` rendering to native

## Safety
- Added to `VisionSafetyManager` method `create(BaseVisionManager)`, property `visionSafetyListener`. `visionSafetyListener` is held as a weak reference.
- Deprecated `VisionSafetyManager` method `create(BaseVisionManager, VisionSafetyListener)`

## v0.8.1

### Vision
- Fixed crash on `VisionManager.create()` with custom `VideoSource`

## v0.8.0

### Vision
- Start monitoring performance related device info

## v0.7.1

### Vision
- Fixed ModelPerformanceMode.DYNAMIC not taking effect with ModelPerformanceConfig.Merged
- Fixed detections of sign objects

## v0.7.0

### Vision
- Improved lane detection
- Fixed swapped top and bottom coordinates in `Detection.boundingBox`
- `FrameStatistics` renaming `FPS` -> `Fps`
- Improve performance of `VisionReplayManager` 

## v0.6.0

### Vision
- Added `currentLaneCenter`, `currentLaneWidth` to `RoadDescription` 
- Renamed `currentLanePosition` to `relativePositionInLane` in `RoadDescription`

## v0.5.0

### Vision
- Added support for UK country
- Added method `Lane.contains(worldCoordinate: WorldCoordinate)`
- Added methods `WorldDescription.getObjectsInLane(lane: Lane)` and `getObjectsOfClass(detectionClass: DetectionClass)`
- Changed implementation of lane detector: it has better quality and improved energy efficiency. Only one ego lane is detected right now
- Changed World-Pixel transformation methods to return optional values
- Changed World-Geo transformation methods to return optional values
- Fixed session recording bug when camera parameters where not recorded. 

## v0.4.2

- Fixed wrong objects' location send to server

## v0.4.1

### Vision
- Changed behaviour on simultaneous `VisionManager`
 and `VisionReplayManager` instances creation to throwing an exception
- Fixed wrong `CameraParams` in replay mode (reason for incorrect AR lane display)
- Fixed possible crash on `VisionSafetyManager`/`VisionArManager` `create`/`destroy`

## v0.4.0

### Vision
- Added `startRecording` and `stopRecording` methods on `VisionManager` to record sessions.
- Added `VisionReplayManager` class for replaying recorded sessions.
- `Detection.boundingBox` now stores normalized relative coordinates.

### VisionAr
- Added `VisionArManager.setLaneLength` method to customize the length of `ArLane`.
