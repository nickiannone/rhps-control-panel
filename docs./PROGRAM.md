RHPS Control Panel program design
========================================

# Software Requirements Analysis

* We want the software system to be smart enough to start itself and clean itself up,  responsive enough to coordinate with actors' movements, and controlled enough to be able to be fixed from the light board.
* There will be two electronic components which communicate with each other: the Screen module and the Lightboard module.
* The two modules should start up when powered on, and move automatically into full functionality and be connected with each other.
* If they are disconnected, they should try to reconnect infinitely before recovering the system status off the wire.
* They will communicate via short messages which relay the full system state at regular, tight intervals (multiple times per second).
* The Lightboard module can change the selected state properties and send them back to the Screen module, which will result in immediate override of the Screen module's state, but the Screen module controls the flow of the show, so transitions happen in a natural way that isn't jarring to the viewers.
* In the event of brownout or power loss, the modules will reset to initial state, but try to figure out the system state from the radio connection, with the Screen module being the source of truth.
* Video loading delay will be compensated for by the module to match up with the running video timer to within a specified tolerance (in ms).
  * How do we achieve this? Can we use compressed video files or do we need MJPEG streams or something?

## Modes of Operation

There are two modes of operation:
* Show Mode
* Manual Mode

### Show Mode

* Upon system power on, start up screen and show Lips splash.
* Start input capture, wait for input from control panel to start show.
* Start show scene state machine at the first scene, and blank the screen.
* Wait for the SHOW_STARTED signal from the lightboard, then enter the running show state.
* Once the lever is pulled, load the scene and play it on the screen, then shut it off after the clip is done and load a blank screen.
  * During any screen transition, a short clip of TV static is played to signify changing channels and stall for loading the video.
* If the lever is pulled again while the screen is on, it will cut the video short and immediately shut off and switch to a blank screen.
* After a scene ends, the next scene is queued up and can be started from the lever or the lightboard module.
* This continues until the end of the show, at which point the system remains on a blank screen unless changed from the lightboard module.

### Manual Mode

The manual mode is the same as the show mode, except the next scene is not automatically selected after a scene ends. Scenes must be
triggered and moved between via the lightboard module.

## System Properties

* SHOW_MODE (bool)
  * Tells what mode the show is in; true = Show Mode, false = Manual Mode.
* SHOW_STARTED (bool)
  * Tells whether or not the show has started.
* SCENE_PLAYING (bool)
  * Tells whether the current scene is playing.
* SCREEN_TRANSITIONING (bool)
  * Tells whether the screen is transitioning (static animation playing).
* SCENE_INDEX (enum)
  * Tells which scene is currently playing. Scenes are indexed starting from 1. 0 indicates no scene is playing (pre-show).
* SCENE_OFFSET_MS (int)
  * Tells the offset into the current scene video, in milliseconds. Expected to be within 1/15ths of a second tolerance (67ms).
* SCENE_LENGTH_MS (int)
  * Tells the length of the current scene video, in milliseconds. Equal to video length (seconds) * 1000.
* CONTROL_BIT (bool)
  * Indicates that this message should be taken as a control signal; when received, should change the system state to match the given properties as quickly as possible.

## State Machine

TODO

# Software Design

TODO

# Development Iterations

* Build screen module prototype
* Load and play video files/MJPEG streams on screen
* Load and seek to random points in the file
* Capture input from the lever
* Trigger video playback from a control program
* Build state machine
* Test transitions between states
* Build lightboard module prototype
* Test lightboard communication protocol use-cases
* Connect lightboard to screen
* Add mode switching
* Add manual mode
* Test against DVD of Rocky
* Add and test backup systems
