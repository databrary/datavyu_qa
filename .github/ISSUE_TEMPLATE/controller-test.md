---
name: Controller Test
about: Test Datavyu Video Controller behavior
title: ''
labels: ''
assignees: ''

---

#### Add Data
Test to make sure Datavyu is able to load videos in all supported plugins. You may use the FrameCounter videos to test different resolutions/formats.

- [ ] Open new instance of Datavyu.
- [ ] On the Controller window, click Add Data.
- [ ] Choose video file to open.
- [ ] On success a new video player window should open up.
- [ ] Test adding multiple videos to the same Controller window.
Check to make sure the tracks area of the Controller window is properly populated with each stream.

#### Playback functions
Test the following playback functions using the appropriate hotkeys.
1. Play
   - [ ] Controller state moves to 1x forward playback, regardless of current speed/state.
   - [ ] Playback is smooth without visible jittering or jumping. Ensure this is the case for long durations of continuous playback (e.g., 30s, 60s).
   - [ ] Compare to playback in a media player (e.g., QuickTime, VLC) if comparison is needed.
1. Shuttle forward/backward
   - [ ] Shuttle forward moves playback speed to the next forward playback increment.
   - [ ] Shuttle backward moves playback speed to the next backward playback increment.
   - [ ] Playback increments are powers of 2 for exponents [-5..5]. There are negative as well as positive increments. Shuttle backwards from zero moves to -1/32x speed.
   - [ ] Smooth playback is expected for playback up to 2x speed.
   - [ ] Playback at speeds faster than 2x should function as required but the quality of the playback may degrade. However,frames should continually update—there should be no “hanging” on a particular frame.
   - [ ] Smooth playback consists of steady frame updates, no jitter,and no visible frame jumping.
1. Stop
   - [ ] Controller moves to 0x playback speed.
   - [ ] All videos stop playing.
   - [ ] No jump in videos before the stop* (this may be broken).
1. Pause
   - [ ] Playback stops immediately.
   - [ ] Controller state should display previous playback speed with brackets surrounding it.
   - [ ] Pressing Pause again resumes playback at the previous speed and removes brackets from the playback speed display.
   - [ ] No visible jumps in the video when pausing/resuming.
1. Jog forward/backward
   - [ ] Jog forward advances the Controller clock forward to the next multiple of the step increment size.
   - [ ] Jog backward moves the Controller flock backward to the previous multiple of step increment.
   - [ ] A step increment is: ceil(1000/FPS)
1. Jump back
   - [ ] Video jumps backwards by the amount indicated in the “Jump back by” field.
   - [ ] Controller time updates to reflect the jump.

#### Tracks
The right side of the Controller window is the area for the video tracks. A horizontal section should be added each time a new data file is added (a track for each video stream). The left side of each track displays an icon for the plugin used to load the video. Beneath the icon are several function buttons: Lock, View, Volume, Resize, Close.
- [ ] Lock - Prevent the track from moving (via mouse drag) when enabled
- [ ] View - Toggles visibility of the video window for this stream
- [ ] Volume - Vertical slider to adjust the volume for this stream
- [ ] Resize - Fixed value sizes to which to scale this stream’s window
- [ ] Close - Remove the video from the Controller

The blue rectangle denoting a track can be dragged (if the Lock is disabled) to change the stream’s start and end position relative to the Controller clock.

#### Zoom Slider
The horizontal slider on the top-right area of the Controller window scales the granularity of the tracks display. Zooming out all the way should show all tracks, beginning to end. Zooming in should scale the tick marks at the bottom edge of the tracks area. Playing while zoomed in should move the needle past the appropriate section.

#### Playhead Needle
The vertical red line in the Controller window’s track area designates the location of the current time in the video tracks. Ensure that dragging the Needle (by right-clicking and dragging the red triangle attached to the top of the Needle) updates the clock and the video windows properly. During playback, the Needle updates and moves along the tracks area.
