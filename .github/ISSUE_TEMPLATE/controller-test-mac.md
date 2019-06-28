---
name: Controller Test Mac
about: Test Datavyu Video Controller behavior
title: ''
labels: 'Platform: Mac'
assignees: ''

---

#### Add Data
Test to make sure Datavyu is able to load videos in all supported plugins. You may use the FrameCounter videos to test different resolutions/formats.

1. Open new instance of Datavyu.
2. On the Controller window, click Add Data.
   - [ ] __Success:__ File chooser window opens up above other windows. The starting folder is the folder containing the last video added to the Controller if there are any, otherwise the user's home folder. The window contains a plugin selection drop-down menu at the bottom of the screen that defaults to FFMPEG. Video files in the current directory are selectable.
3. Choose video file to open.
   - [ ] __Success:__ a new video player window opens up. The player window displays the first frame of video, or the frame at the current needle position if the needle is not at the start of the track.
4. Test adding multiple videos (using the same plugin) to the same Controller window.
   - [ ] __Success:__ Each file added creates a new track in the Controller window and a new video player window. **Check to make sure the tracks area of the Controller window is properly populated with each stream**.
5. Test resizing video windows.
   - [ ] __Success:__ Video windows change size without distortion or cropping. Areas of the player window without the video frame is padded black.

Note: If there are multiple Video Plugins, repeat steps from 2 to 5 with each plugin. Macs should have both the FFMPEG and NativeOSX plugins.

#### Playback functions
Test the following playback functions using the appropriate hotkeys or Video Controller buttons.
1. Play
   - [ ] Controller state moves to 1x forward playback, regardless of current speed/state.
   - [ ] Playback is smooth without visible jittering or jumping. Ensure this is the case for long durations of continuous playback (e.g., 30s, 60s).
   - [ ] Compare to playback in a media player (e.g., QuickTime, VLC) if comparison is needed.
1. Shuttle forward/backward
   - [ ] Shuttle forward moves playback speed to the next forward playback increment (See [Playback speeds table](https://github.com/databrary/datavyu_qa/wiki/Resources/_edit#playback-speeds)).
   - [ ] Shuttle backward moves playback speed to the next backward playback increment (See [Playback speeds table](https://github.com/databrary/datavyu_qa/wiki/Resources/_edit#playback-speeds)).
   - [ ] Smooth playback is expected for playback up to 2x speed.
   - [ ] Playback at speeds faster than 2x should function as required but the quality of the playback may degrade. However,frames should continually update—there should be no “hanging” on a particular frame.
   - [ ] Smooth playback consists of steady frame updates, no jitter,and no visible frame jumping.

   **Notes:**
    - Backward Playback with FFmpeg plugin shows stuttering from [-1/32..-4] speeds, this behavior is acceptable for a backward playback.
    - Playback increments are powers of 2 for exponents [-5..5]. There are negative as well as positive increments. Shuttle backwards from zero moves to -1/32x speed (See [Playback speeds table](https://github.com/databrary/datavyu_qa/wiki/Resources/_edit#playback-speeds)).


1. Stop
   - [ ] Controller moves to 0x playback speed.
   - [ ] All videos stop playing.
   - [ ] No jump in videos before the stop* (this may be broken).
   - [ ] Play again and confirm that the Video Controller State is correct (Go through the checklist again).
1. Pause
   - [ ] Playback stops immediately.
   - [ ] Controller state should display previous playback speed with brackets surrounding it.
   - [ ] Pressing Pause again resumes playback at the previous speed and removes brackets from the playback speed display.
   - [ ] No visible jumps in the video when pausing/resuming.
   - [ ] Repeat steps with different playback speeds (No need to go through every playback speed one positive and one negative shuould be enough)
1. Jog forward/backward
   - [ ] Open counter.mp4 video (Download the resource from [here](https://github.com/databrary/datavyu_qa/wiki/Resources/_edit#videos)).
   - [ ] Jog forward advances the Controller clock forward to the next multiple of the step increment size (See Note).
   - [ ] The counter video advances by one frame.
   - [ ] Jog backward moves the Controller clock backward to the previous multiple of step increment (See Note).
   - [ ] The counter videos step back by one frame.

   **Note:** A step increment is: ceil(1000/FPS)
1. Jump back
   - [ ] Video jumps backwards by the amount indicated in the “Jump back by” field.
   - [ ] Controller time updates to reflect the jump.

#### Tracks
The right side of the Controller window is the area for the video tracks. A horizontal section should be added each time a new data file is added (a track for each video stream). The left side of each track displays an icon for the plugin used to load the video. Beneath the icon are several function buttons: Lock, View, Volume, Resize, Close.
- [ ] Lock - Prevent the track from moving (via mouse drag) when enabled
- [ ] View - Toggles visibility of the video window for this stream
- [ ] Volume - Vertical slider to adjust the volume for this stream
- [ ] Resize - Fixed value sizes to which to scale this stream’s window
-  Close - Remove the video from the Controller
  - [ ] __Success:__ The track is removed from the Controller and other tracks (if any) are shifted to take up its space. The player window closes and leaves no traces behind.
- [ ] Stop the player and move the track after the playback needle: the player seeks and displays the first frame.
- [ ] Play and wait until the needle reaches the beginning of the track.
- [ ] Move the track before the needle: the player should seek and display the last frame.
- [ ] Stop the player, move the needle just before the end of the track (e.g. 5 seconds) and play: the player should stop at the last frame when the needle passes the track.
- [ ] Reset the track to its original position and put the playhead needle somewhere in the middle of the track.
- [ ] Set a region around the needle by moving the two green bars at the sides of the video tracks area.
- [ ] Play forward and backward at different speeds: the player should pause at the boundary of a region (See Pause section for the state of the Video Controller).
- [ ] When the needle is at a boundary (a green bar) move the latter: the Video Controller should stay at Paused State.

**Note:** The blue rectangle denoting a track can be dragged (if the Lock is disabled) to change the stream’s start and end position relative to the Controller clock.

#### Zoom Slider
The horizontal slider on the top-right area of the Controller window scales the granularity of the tracks display.
- [ ] Zooming out all the way should show all tracks, beginning to end.
- [ ] Zooming in should scale the tick marks at the bottom edge of the tracks area.
- [ ] Playing while zoomed in should move the needle past the appropriate section.

#### Playhead Needle
The vertical red line in the Controller window’s track area designates the location of the current time in the video tracks.
- [ ] Ensure that dragging the Needle (by right-clicking and dragging the red triangle attached to the top of the Needle) updates the clock and the video windows properly. During playback, the Needle updates and moves along the tracks area.

#### Notes
- If Datavyu is not installed on your machine, please follow [Installation Instructions](https://github.com/databrary/datavyu_qa/wiki#installation)
